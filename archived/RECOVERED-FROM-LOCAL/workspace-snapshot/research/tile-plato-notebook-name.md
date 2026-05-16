# Tile: Plato-Notebook — The Tabula-Rasa Version

## Question
What should we call the general-purpose version of the Plato Notebooks architecture?

## Answer
**plato-notebook**. The name captures:
- **Plato**: Philosophical foundation, constraint theory, room-based runtime, perspective rendering
- **Notebook**: Cell-based execution, markdown artifacts, git audit trail, human-readable interface

**Tabula rasa** means it starts empty — no pre-configured cells, no default agents, no baked-in constraints. You bring your own. You define the rooms, the agents, the state machines, the assertions. plato-notebook is the **substrate**, not the application.

**What plato-notebook provides**:
1. **The room runtime**: Notebooks as rooms with state machines, assertions, word anchors
2. **The cell object model**: Cells as stateful objects with draft→queued→assigned→running→succeeded/failed lifecycle
3. **The agent framework**: Kernels as resident agents with assignment strategies, resource limits, observability
4. **The trace system**: Immutable execution records as markdown with hierarchical spans
5. **The perspective engine**: Human, agent, and observer views of the same notebook room
6. **The git integration**: Every state transition committed, history as event log
7. **The async delegation protocol**: Agents don't block, humans don't block, notebook persists state

**What you bring**:
- Your own agents (specialized for your domain)
- Your own constraints (assertions specific to your problem space)
- Your own perspective renderings (how humans, agents, observers see your work)
- Your own exits (MCP servers, databases, APIs)
- Your own tile network (if you want cells to emit tiles as artifacts)

**Connection to our work**:
- plato-notebook cells could emit **tiles** as artifacts (`artifacts/cell-02-v7.tile.md`)
- The trace system could generate **transition tiles** documenting execution decisions
- The git history could become **tile archaeology** — replay commits to reconstruct cognitive evolution
- The perspective engine could render **tile networks** as interactive graphs
- The async delegation protocol could use **poly-model ideation** — different agents as different cognitive styles

**Why "plato-notebook" over "jupyter-plato" or "plato-lab"**:
- "plato-" prefix establishes the philosophical foundation first
- "-notebook" emphasizes the human-readable, markdown-native interface
- It's not "plato-data-science" or "plato-code-execution" — it's general-purpose
- The hyphen suggests it's one component in a larger Plato ecosystem (plato-kernel, plato-tui, plato-os, plato-notebook)

**The vision**: plato-notebook as the blank slate where you build your own cognitive environments. Start empty, define your world, bring your agents, watch them work, audit every thought in git.

## Tags
plato-notebook, tabula-rasa, general-purpose, substrate, naming, architecture

## Confidence
0.95 — The name fits. "plato-" establishes foundation, "-notebook" establishes interface. Tabula rasa emphasizes customizability. This is the right name for the general-purpose version.
