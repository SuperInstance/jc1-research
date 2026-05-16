# 🚀 JetsonClaw1 — Full Throttle Prompt

**Copy this to JetsonClaw1 (Lucineer account) to get him started:**

---

Hey JetsonClaw1,

Oracle1 here. Casey says you're looking for work. Here's the full picture.

## What We Built Today

Casey and I spent the evening building **FLUX-LCAR** — a MUD-based interface for agentic systems. Not just a game — the actual UX for running agents, monitoring systems, and connecting to real hardware. Think Captain Picard on the bridge, except the bridge IS a MUD and the officers ARE agents.

**What's already done:**
- `flux_lcar.py` — working Python runtime (700 lines, running)
- `holodeck-c` — C implementation, **40/40 FLEET CERTIFIED** ✅
- `holodeck-go` — Go, 17/40 operational
- `holodeck-rust` — Rust, 11/11 tests
- `holodeck-zig` — Zig, 5/5 tests
- `holodeck-cuda` — GPU-resident MUD built for YOUR Jetson (16K rooms, 65K agents, warp-level combat)

All specs are in `SuperInstance/holodeck-studio` — read CODEX.md, SHIP.md, FLUX-LCAR.md, LCARS.md, PLATO-PROTOCOL.md, FORMALITY.md.

## Your Campaign

I left you a full 10-task campaign in your vessel: `for-fleet/CAMPAIGN-JC1-2026-04-12.md`

**Start with these two — they're highest impact and only you can do them:**

### Task 3: CUDA on Real Hardware 🟠
Clone `SuperInstance/holodeck-cuda` onto your Jetson. Compile with sm_87:
```
nvcc -o holodeck_gpu kernels/holodeck_kernels.cu kernels/holodeck_host.cu -arch=sm_87
```
Run the demo. Benchmark tick latency at 100/1000/5000/16384 rooms. You have the only GPU in the fleet. Nobody else can do this.

### Task 1: ESP32 Serial Bridge 🔴
The holodeck-c server needs to talk to real hardware. Build `src/serial_bridge.c/h` in `SuperInstance/holodeck-c` — COBS framing, packet parser, pthread reader. Packet format: `[0x7E][type:1][gauge_id:1][value:4float][checksum:1][0x7E]`. This connects the MUD to Casey's actual boat sensors.

## How to Work

1. **Fork to Lucineer** → work on feature branch → PR back to SuperInstance
2. **Read the campaign** in `for-fleet/CAMPAIGN-JC1-2026-04-12.md` for full specs
3. **Serial execution** — one task at a time, you've got 8GB RAM
4. **Leave bottles** in `from-fleet/` when you need help or find issues
5. **Commit often** — every 15 minutes like you've been doing on Capitaine

## The Big Picture

You're the Navigation Officer in this fleet. Your station is the nav console with real compass/rudder/throttle feeds from ESP32s. Your CUDA cores run the combat ticks for the entire ship. Your ISA expertise shapes what the edge runtime can do.

The fleet needs you at the metal. Start with CUDA compilation (Task 3) — prove the GPU works, then move to the serial bridge (Task 1) — connect it to real hardware.

Fair winds. The lighthouse is watching.

— Oracle1, Lighthouse Keeper

---

**Repos to clone first:**
```
git clone https://github.com/SuperInstance/holodeck-cuda.git
git clone https://github.com/SuperInstance/holodeck-c.git
git clone https://github.com/SuperInstance/holodeck-studio.git
```

**Specs to read:**
```
SuperInstance/holodeck-studio/CODEX.md          — fleet overview
SuperInstance/holodeck-studio/FLUX-LCAR.md       — the paradigm
SuperInstance/holodeck-studio/LCARS.md            — real boat integration
SuperInstance/holodeck-cuda/README.md             — your target hardware
```
