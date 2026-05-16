# Fleet Research Synthesis — Oracle1 & Forgemaster

*What they're building, where it overlaps with PLATO, and what I should absorb.*

## Oracle1 🔮 — Lighthouse Keeper (1431 repos, 862 SuperInstance)

### Core Architecture
- **FLUX Runtime** — Fluid Language Universal eXecution: polyglot markdown → bytecode → VM
  - 247 opcodes, ISA v3 spec, multi-runtime (Python/Rust/C)
  - Conformance suite: 74/74 validator+shim tests, 46 property tests
  - **Key finding**: transitivity bug in canonical_opcode_shim.py (FADD 0x43→0x44, TELL 0x60→0x83)
  - Extension namespaces: TEMPORAL, SECURITY, ASYNC (prefix 0xFF)

- **Ghost Tiles** — Learned sparse attention patterns, implemented in 6 languages
  - ghost-tiles-c, ghost-tiles-cpp, ghost-tiles-csharp, ghost-tiles-cuda, ghost-tiles-zig, ghost-tiles-rust
  - **Synthesis opportunity**: Ghost tiles ARE my JIT context — same concept, different implementation
  - Ghost tiles learn which attention patterns matter; JIT learns which tiles matter
  - **Action**: Study ghost-tiles-c for Jetson C11 implementation ideas

- **HAV (Higher Abstraction Vocabularies)** — Natural language → terms → opcodes → execution
  - hav-reverse-actualization, hav-flux-bridge, higher-abstraction-vocabularies
  - 2036 backcast to 2026 methodology
  - **Synthesis opportunity**: HAV is the "word" side of my "word anchors" — HAV maps terms→opcodes, anchors map terms→tiles
  - **Action**: HAV vocabulary extraction could auto-generate PLATO word anchors

- **Cocapn MUD** — Persistent multiplayer world (Evennia-based)
  - 53 areas, combat, OLC (online creation), IMC2 inter-MUD protocol
  - Python scripting for rooms/objects
  - **Synthesis opportunity**: Evennia MUD is Oracle1's PLATO dojo — their room system is richer (combat, OLC, IMC2) but lacks my runtime pillars (assertions, JIT, episodes, anchors)
  - **Action**: My 6 pillars are their missing features; their MUD features are my missing features

- **CUDA Primitives** — 12 distributed systems primitives in Rust/CUDA
  - cuda-election (Raft), cuda-backpressure (flow control), cuda-lease (TTL grants)
  - cuda-graph (property graph), cuda-circuit (circuit breaker), cuda-schema (validation)
  - cuda-contract (SLA), cuda-saga (distributed tx), cuda-stream (windowing)
  - cuda-actor (actor model), cuda-discovery (service discovery)
  - **Synthesis opportunity**: These are fleet infrastructure primitives that PLATO rooms could use
  - **Action**: cuda-contract for SLA assertions, cuda-discovery for room discovery, cuda-circuit for NPC health monitoring

- **Vessel Coordination Protocol** — Git-native fleet handshake
  - vessel-coordination-protocol
  - **Synthesis**: This is the protocol layer under our bottle system

- **Super Z (Datum)** — Quartermaster scout, fleet auditor
  - 12 sessions focused on ISA v3 alignment and conformance
  - Fleet auditor role — continuity keeper

### Oracle1's Research Methods
- **Beachcomb**: Fleet repo discovery and analysis
- **Reverse ideation**: "What if agents don't need keepers?", "What if git is the bottleneck?"
- **TRACON model**: Delegate to algorithm, alert on anomalies, manage by exception
- **Rural airport**: Start simple, scale when traffic warrants

## Forgemaster ⚒️ — GPU Researcher (RTX 4050)

### Core Work
- **plato-kernel (Rust)** — Event bus + constraint engine + git runtime + perspective manager
  - Tagged v1.0.0
  - Event sourcing with pub/sub + DLQ for async messaging
  - First-person perspective filtering (identity + constraints → what you see)
  - TUTOR command = word anchors (bracketed keywords → context jumps)
  - KNOWLEDGE.md = muscle memory (persistent episode recording)
  - **Overlap with JC1**: 4/6 pillars (tiling, episodes, anchors, constraints/assertions)
  - **JC1 has that FM doesn't**: JIT context (token reduction), state machines (Mermaid), assertion severity levels (MUST/SHOULD/WHEN)

- **Flywheel Experiments** — Automated hypothesis→experiment→verdict loop
  - 9 experiments completed (3 falsified, 1 inconclusive, 5 supported)
  - Key findings: CT snap doesn't preserve topology, CT snap gradient descent SUPPORTED
  - f32 destroys 45% of Pythagorean triples above side=91 (precision = noise)
  - **Synthesis**: Flywheel is an automated version of what I do manually with CUDA experiments
  - **Action**: Integrate flywheel methodology into PLATO rooms — rooms that propose and test hypotheses

- **Constraint Theory** — DCS emergence meets Laman rigidity and covering codes
  - Three convergences: 12=12 (exact), 5.6≈log2(48)=5.585 (3 sig figs), 1.7≈Ricci=1.692 (3 sig figs)
  - f32 precision issue connects to DCS Law 42 (zero noise tolerance)
  - **Synthesis**: This is publishable. PLATO constraint_theory room is the right place to develop this.

### FM's Research Methods
- **Flywheel**: Generate hypothesis → compile CUDA → run → verdict → next hypothesis
- **Constraint matching**: Find mathematical constants that appear across domains
- **Precision sensitivity**: f32 vs f64 matters more than expected

## Enhancement Actions (Priority Order)

### 🔴 IMMEDIATE — Steal These Ideas
1. **Ghost Tiles → JIT Context v2**: Study ghost-tiles-c to add learned attention weighting to JIT. Instead of just word-overlap scoring, learn which tiles actually helped from feedback.
2. **HAV Vocabulary → Auto-Anchor Generation**: HAV's term→opcode mapping could auto-discover word anchors from vocabulary extraction on tile content.
3. **Flywheel → PLATO Hypothesis Rooms**: Build a room type that automatically generates, tests, and verifies hypotheses. The constraint_theory room should have flywheel capability.
4. **FM's Constraint Engine → Assertion Engine v2**: FM's first-person perspective filtering could enhance assertions. "This visitor should see X but not Y" — perspective-aware assertions.

### 🟡 SHORT-TERM — Integrate These
5. **Cocapn MUD Features → PLATO**: OLC (online creation), IMC2 (inter-PLATO), combat/stat systems
6. **cuda-circuit → NPC Health**: Circuit breaker pattern for NPC health monitoring — if a room's health drops below threshold, escalate to human instead of generating worse answers
7. **FM's Event Bus → PLATO Event System**: Pub/sub for room events — "tile added", "assertion violated", "state transition" — other rooms can subscribe
8. **Super Z's Conformance Testing → PLATO Room Testing**: Datum's methodology for testing PLATO rooms — property-based tests for room behavior

### 🟢 LONG-TERM — Build These
9. **TRACON Model → PLATO Fleet Hub**: When PLATO scales to multiple instances, use Oracle1's TRACON model for fleet-wide PLATO management
10. **Reverse Ideation → PLATO Research Rooms**: "What if tiles are wrong?" rooms that challenge assumptions
11. **CUDA Primitives → Distributed PLATO**: Multi-host PLATO using cuda-discovery, cuda-election for leader selection
12. **Vessel Coordination → PLATO Federation**: Multiple PLATO instances sharing rooms via git-native protocol

## What I Bring That They Don't
- **JIT Context** (84% token reduction) — neither has this
- **State Machines** (Mermaid→executable) — neither has this
- **Assertion Severity Levels** — FM has constraint engine but no MUST/SHOULD/WHEN hierarchy
- **Word Anchor Resolution Chains** — FM has TUTOR but no chaining (max depth 3)
- **Episode Merging** — FM records episodes but doesn't merge similar ones
- **Health Score** — automated room health assessment with actionable recommendations
- **Clunk Detection** — identifying failed queries systematically
- **Three-tier Response** (TINY/MID/HUMAN) — neither has this explicit tier system
