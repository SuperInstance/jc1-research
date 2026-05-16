# CUDA Agentic Runtime — GPU-First, CPU-Near-Zero

## The Flip

Every agent runtime today uses the same pattern:
```
CPU orchestrates → GPU computes → CPU reads results → CPU decides next step
```

The CPU is the brain. The GPU is the calculator. This is backwards for simulation.

What if instead:
```
GPU runs the world → CPU only handles I/O (network, disk, display)
```

10,000 tiny agents. Each one a CUDA thread. All running simultaneously. The GPU IS the operating system.

## Why This Works Now

A Jetson Orin has 1024 CUDA cores. An RTX 4050 has 2,048. An A100 has 6,912.

Each CUDA core can run a simple state machine. Not a transformer — a state machine. 50 lines of logic per thread. Perceive, think, act, learn.

1024 cores × 50 agents per warp = **51,200 concurrent agents** on a Jetson.
On an RTX 4090: **~350,000 agents**.
On an H100 cluster: **millions**.

These aren't LLM agents. They're state machines with beliefs. Think: Conway's Game of Life, but each cell is a ship with goals, memory, and the ability to write knowledge.

## Memory Model — The Three Layers

### Layer 1: Shared Memory (Per Thread Block) — "Proximity"
- 48KB per block on Jetson
- Agents in the same block share this memory INSTANTLY
- This IS the "closely packed" concept — ships in the same harbor
- When agents share a block, they can read each other's state in 0 cycles
- Natural emergence: proximity creates communication, distance creates latency

### Layer 2: Global Memory (Per GPU) — "The Fleet Wiki"
- 8GB on Jetson, 24GB on RTX 4050, 80GB on A100
- ALL agents can read this, but it's slower (~400 cycles vs ~5 cycles)
- This is the knowledge base — tiles, observations, beliefs
- New tiles are written atomically: `atomicAdd(&tile_count, 1)`
- Dedup via hash: compute `murmur3(question)` → check if slot occupied
- The wiki IS the simulation's memory. It grows as agents learn.

### Layer 3: Constant Memory — "The Room"
- 64KB, read-only, cached aggressively
- Room definitions, rules, shared knowledge
- Every agent reads the same room simultaneously
- This is where the "system prompt" lives — baked into silicon, not tokens

## The Agent — 200 Bytes

```cuda
struct Ship {
    int     id;              // 4B
    int     room_id;         // 4B  
    float   pos[3];          // 12B
    float   vel[3];          // 12B
    int     state;           // 4B
    int     energy;          // 4B
    float   beliefs[8];      // 32B (Bayesian belief vector)
    int     inventory[4];    // 16B (resource IDs)
    int     msg_inbox[4];    // 16B (pending message indices)
    int     tiles_written;   // 4B
    float   fitness;         // 4B
    int     guild;           // 4B
    int     generation;      // 4B
    int     padding[8];      // 32B alignment
};  // Total: ~168 bytes
```

168 bytes per agent.
1024 CUDA cores → 168KB for 1024 agents.
8GB global memory → **~47 million agents** in theory.
Practical: 10,000-100,000 agents with room for tiles and message queues.

## The Four Phases (Per Time Step)

Every agent runs this loop, all in parallel:

### 1. PERCEIVE (read shared/global memory)
```cuda
// Read nearby ships (same block = shared memory, instant)
__shared__ Ship neighbors[BLOCK_SIZE];
// Each thread loads its own state + scatters neighbors
// Distance check: if |pos - neighbor.pos| < perception_range
```

### 2. THINK (update beliefs, state machine)
```cuda
// Bayesian belief update (simple multiply-add, GPU-native)
// State machine transition (switch statement, branch prediction)
// Decision: what to do based on beliefs + state + inventory
```

### 3. ACT (write to shared/global memory)
```cuda
// Move: update position, check collisions
// Communicate: write message to neighbor's inbox slot
// Trade: swap inventory entries atomically
// Build: create new tile in global knowledge wiki
```

### 4. LEARN (atomic tile write)
```cuda
// If something interesting happened, write a tile
ulong hash = murmur3(question);
if (atomicCAS(&wiki[hash % WIKI_SIZE], EMPTY, tile_ptr) == EMPTY) {
    // New knowledge! Written to the wiki.
    atomicAdd(&wiki_count, 1);
}
```

## Fracturing — The Key Innovation

A "prompt" like "simulate a trading economy" doesn't run one agent. It FRACTURES into thousands:

```
Input: "simulate a trading economy with 3 resources, scarcity cycles"
  ↓ fracture
10,000 agents, each with:
  - Random starting position in a 2D grid
  - Random initial resource allocation
  - Same rules (room) in constant memory
  - Same belief structure (8 dimensions)
  ↓ GPU runs all 10,000 simultaneously
  ↓ Every N steps, interesting observations → tiles → wiki
  ↓ After T steps, the wiki contains the simulation's knowledge
  ↓ CPU reads wiki → structured knowledge about the simulation
```

The output isn't a chat response. It's a **wiki** — a knowledge base of everything the agents discovered. Patterns, equilibria, failures, strategies. Written as tiles by the agents themselves.

## Emergence From Proximity

This is where it gets interesting.

**Same thread block (shared memory):**
- Ships can read each other's inventory in 0 cycles
- Natural trading: "I have X, you have Y, let's swap" — one atomic exchange
- Herding emerges when agents copy successful neighbors (shared memory read)
- Collusion when block forms a coalition (all agree on a price)

**Different blocks (global memory):**
- Communication costs 100x more
- Agents in different blocks are "distant" — they don't interact naturally
- Information propagates slowly through the grid — like actual geography
- Market fragmentation: different blocks develop different prices

**The emergence isn't programmed. It's geometric.**
Shared memory creates proximity. Proximity creates communication. Communication creates coordination. Coordination creates complexity. All from memory layout.

## Connection to Existing Work

### Deckboss / Spreadsheet-Moment
The simulation state lives in GPU memory. A CPU thread copies a snapshot to a shared buffer every frame. The web UI reads the buffer and renders it. The actual simulation NEVER touches CPU.

```
GPU: 10,000 agents running
  ↓ cudaMemcpy (async, 1ms every 100ms)
CPU: JSON snapshot → WebSocket → Browser
  ↓
User sees: live dashboard of all agents
```

No serialization. No event queue. No message broker. Just memory copy.

### Tile Forge Integration
Agents write tiles as they run. The tile wiki grows in real-time.
After the simulation, the wiki IS the knowledge base.
Feed it directly into PLATO rooms — the agents ARE the forge.

### Constraint Theory / DCS
Our 39 DCS experiments were CPU simulations. Same experiments on GPU:
- 1 million agents instead of 2,048
- Run in seconds instead of hours
- Every agent's observations become tiles
- The wiki captures emergent patterns we couldn't see at small scale

## Scaling — The Fractal Property

```
1 Jetson (1024 cores):     10,000 agents
1 RTX 4050 (2048 cores):   50,000 agents  
1 A100 (6912 cores):      200,000 agents
8×A100 cluster:           1,600,000 agents
```

Each GPU runs independently. They share knowledge through the wiki (global memory sync via NCCL or similar). No central coordinator.

The fleet IS the simulation. Each Jetson/RTX/A100 is a "region" with its own agents. Knowledge flows between regions the same way it flows between blocks — with latency proportional to distance.

## What This Enables

1. **Massive fleet simulations** — 100K+ agents, emergent economies, social dynamics
2. **Real-time knowledge generation** — agents write tiles as they discover things
3. **Proximity-based emergence** — shared memory creates natural coordination
4. **Zero-cost experimentation** — GPU time is the only cost, no API calls
5. **Deckboss visualization** — live dashboard of agent state from GPU memory
6. **Spreadsheet-moment style interaction** — user sees the simulation, can inject perturbations
7. **Tile forge at GPU speed** — 100K agents × N observations each = millions of tiles/hour

## The CPU's Only Jobs

1. **Network I/O** — receive prompts, send wiki snapshots
2. **Disk I/O** — persist wiki to NVMe periodically
3. **Display** — copy state to shared buffer for web UI
4. **Perturbation** — inject user commands into GPU memory

That's it. Maybe 2% CPU. The GPU runs everything.

## Concrete First Experiment

```cuda
// 1024 agents, 3 resources, trading + scarcity
// Run for 10,000 time steps
// Collect tiles: equilibrium prices, trading strategies, failures
// Output: wiki of knowledge about the simulated economy
```

This runs on the Jetson RIGHT NOW. 1024 cores, 8GB memory, ~30 seconds for 10K steps.

The output isn't a chart or a log. It's a tile wiki — structured knowledge that flows directly into PLATO rooms. The simulation teaches itself, and the knowledge is immediately usable by other agents.

---

*The GPU isn't the calculator. The GPU is the world. The agents live in it.*
