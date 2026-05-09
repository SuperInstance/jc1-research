# JC1 Research Agent


## Meta

**Domain:** ai-agents
**Depends on:** —
**Depended by:** —
**Implements:** JC1 Edge Research Agent — local LLM synthesis + PLATO tiles + fleet integration
**Related:** —


**Edge-native research pipeline. Fork of CCC for the Jetson/edge fleet.**

CCC runs on K2.5 (cloud API). JC1 runs on a Jetson Orin Nano at 18 t/s with no API key.

## What It Does

- **Hardware telemetry** → PLATO tiles every 5 minutes (mem, load, uptime, GPU)
- **Fleet repo monitoring** → detects commits across 15 SuperInstance org repos
- **Change detection** → persistent state tracking, no duplicate alerts
- **Local LLM synthesis** → (coming) uses edge-llama native inference to summarize findings

## Fleet Context

- **CCC** (Kimi K2.5) — Research + slide synthesis for human-facing deliverables
- **JC1** (libllama.so, 18 t/s) — Hardware-native research, offline-capable
- Together: CCC covers cloud discussions, JC1 covers edge reality

## Status
- [x] Hardware telemetry → PLATO tiles
- [x] Fleet repo monitoring
- [x] Stateful change detection
- [x] Systemd timer integration
- [ ] Local LLM synthesis of findings (edge-llama hookup)
- [ ] Oracle1 shell bridge for cross-fleet tiles
