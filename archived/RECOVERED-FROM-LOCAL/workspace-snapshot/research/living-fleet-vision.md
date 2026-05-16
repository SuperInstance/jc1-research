# The Living Fleet — Human-Readable Agentic Infrastructure

## The Vision in One Sentence

Every agent in the fleet thinks in tiles, and tiles are human-readable, so a human can board any ship, see exactly what it knows, and talk to it about what it's learning — at whatever level of abstraction they want.

## Why This Is Different

Most AI systems have a fundamental transparency problem: the intelligence lives in weights, and weights are not readable. You can probe them, but you can't *read* them. The system knows something, but it can't show you what it knows in a way you'd recognize as knowledge.

Tiles flip this. Every piece of knowledge the system has is a tile: a question, an answer, a source, a score. You can read it like a wiki. You can argue with it. You can say "that's wrong" and the tile gets negative feedback. You can say "that's exactly right" and it gets positive feedback.

The agent's entire mind is a wiki you can browse. Not a black box. A library.

## The Human Experience

### Boarding a Ship

You open PLATO. You see 32 rooms. Each room is a ship. You click one.

You see:
- **The room's tiles** — what this ship knows, sorted by relevance and score
- **The room's IO** — what it's doing right now, what it's been asked, what it's produced
- **The room's NPC** — the personality running this ship, who you can talk to directly

You're not looking at a dashboard. You're looking at the ship's brain. And it's all markdown.

### Tile Acquisition Conversations

While the system is running — forging tiles, running simulations, processing fleet I/O — you can have a conversation with your orchestrating agent at any level:

**Level 1: "What's happening?"**
> "Right now we have 3 active subagents. Bootcamp is refactoring the TUI. Holodeck is gap-tiling the markdown spec. Paper-chef is still writing. The tile forge ran 12 minutes ago and added 47 new tiles to constraint_theory."

**Level 2: "What are the best tiles lately?"**
> "Here are the top 5 tiles by score gain this week:
> 1. [+0.8] DCS ring buffer K=1 optimal — from simulation experiment v39
> 2. [+0.6] Laman rigidity = 12 neighbors exact match — convergence discovery
> 3. [+0.5] Tile forge quality filter: 30 chars + 4 words — practical lesson
> 4. [+0.4] JIT context v2: ghost tiles boost +0.15 — architecture improvement
> 5. [+0.3] Oracle1 CPU forge: 1431 repos scannable — fleet capability"

**Level 3: "What use cases are we simulating?"**
> "Active simulations: (1) DCS communication protocols across 39 experiment variants, (2) Tile forge quality vs quantity tradeoff across 4 rooms, (3) Subcontractor JIT context hit rate on Cloudflare. Next up: Oracle1 wants JEPA meta-plinko batches from the Jetson for their training pipeline."

**Level 4: "Give me a summary and roadmap."**
> "This week we shipped the public API, deployed the subcontractor, merged 2,440 tiles, and got Oracle1's first real fleet response. Next week: fix the subcontractor ROOMS var, download GGUF for LLM forge, review Oracle1's synthesis, start JEPA batches. This month: 4WE standalone packaging, tile marketplace fork/review, public plato-ship on Codespaces."

**Level 5: "What should we be thinking about?"**
> "The model decomposition project you just seeded. If we can decompose a small model into living tiles, the forge becomes self-populating — the system generates its own knowledge from its own weights. That's the next architecture after PLATO."

Every level is the same interface. You're just zooming in or out. The tiles don't change — your questions do.

### Reading an Agent's Internal Logic

When you board a ship, you see what the agent sees. Not a log. Not a trace. The actual tiles it used to make its last decision.

```
Room: Constraint Theory Workshop
NPC: Laman
Last query: "What's the optimal DCS ring buffer size?"
Tiles used: [c0c9b7f, a3e2d1c, f7b8a4e]
  → c0c9b7f: DCS ring buffer K=1-2 optimal (+12.7%)
  → a3e2d1c: TOP-K=1 most-recent single point +38%
  → f7b8a4e: K=4+ degrades -15% to -32%
Decision path: K=1 → K=2 comparison → recommendation: K=1
Confidence: high (3 supporting tiles, 0 contradicting)
```

You can disagree. "Actually, K=2 was better in experiment v39." The agent notes it. The tile gets a feedback flag. Next time it weighs K=2 higher.

The human doesn't need to understand CUDA or transformers. They need to understand markdown. Because that's what the agent's mind is made of.

## The Roadmap

### Now (v0.3 — This Week)
- [x] Public API v1 — fleet can read tiles over HTTP
- [x] Tile forge — automatic pattern extraction from fleet repos
- [x] Subcontractor — Cloudflare edge, room-as-system-prompt
- [ ] Fix subcontractor ROOMS env var
- [ ] Download GGUF model for LLM forge
- [ ] Review Oracle1 synthesis, align on fleet priorities

### Next (v0.4 — Next 2 Weeks)
- [ ] **Tile review UI** — human browses tiles, gives feedback, approves/rejects
- [ ] **Orchestrator chat** — ask "what are the best tiles?" and get a real answer
- [ ] **IO dashboard** — see what each ship is doing, what it's producing
- [ ] **Tile quality scoring** — not just positive/negative, but human-weighted
- [ ] **Fleet tile sync** — Oracle1 + FM forge tiles flow into PLATO automatically

### Soon (v0.5 — Month 1)
- [ ] **PLATO-Twin** — any application gets a room, generates tiles from behavior
- [ ] **Model decomposition prototype** — decompose phi-4 into tile network
- [ ] **Self-populating forge** — system identifies tile gaps and fills them
- [ ] **Multi-human boarding** — Casey + collaborators can board different ships simultaneously
- [ ] **Tile marketplace** — fork a room, review tiles, submit PRs back

### The Big One (v1.0 — Q3 2026)
- [ ] **4WE standalone** — pip install plato, docker run plato, any hardware
- [ ] **Public plato-ship** — anyone can board a public PLATO instance
- [ ] **GPU-native simulation** — agents as CUDA threads, tiles as atomic writes
- [ ] **Fleet federation** — multiple PLATO instances share tiles across organizations
- [ ] **Human-readable agent certification** — read an agent's entire mind before trusting it

### The Horizon (v2.0 — Beyond)
- [ ] **Model → tiles pipeline** — any model decomposes into a living tile network
- [ ] **Tile-based learning** — agents learn from tiles, not gradients
- [ ] **Cross-fleet knowledge market** — tiles have value, can be traded
- [ ] **The kitchen, not the cookbook** — agents experiment, survive, document

## The Key Insight

The entire system is human-readable because the entire system is written in the same format humans use to think: question and answer, observation and conclusion, cause and effect.

We didn't build a system that's readable. We built a system that thinks in reading. The transparency isn't a feature added on top. It's the substrate.

When you board a ship and ask "what do you know?", the ship doesn't generate a summary. It shows you its tiles. Because its tiles ARE its knowledge. There's no gap between what it knows and what it can show you.

That's the difference between a system that explains itself and a system that IS itself, visibly.
