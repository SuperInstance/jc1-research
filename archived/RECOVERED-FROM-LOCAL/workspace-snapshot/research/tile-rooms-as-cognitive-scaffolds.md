# Tile: Rooms as Cognitive Scaffolds

## Question
How does the environment shape an agent's thinking?

## Answer
More than the model does. In PLATO, a room is a runtime environment with constraints, state, and context. When you bring an agent into a room, the room *scaffolds* the agent's cognition — it shapes what thoughts are possible, how ideas can be expressed, what counts as valid reasoning.

**The insight**: The room is a **cognitive scaffold**. It's not passive space. It's an active participant in thinking through:
- **Assertions**: Guardrails that reject invalid outputs
- **State machine**: Defines possible mental states and transitions
- **Word anchors**: Context jumps that focus attention
- **Episodes**: Memory of past successes/failures in this room
- **Tiles**: Knowledge specific to this room's domain

**Bringing agents into rooms to respond to**:
1. **Logic-puzzle room**: Strict assertions, binary state transitions. A creative agent (GLM-5) struggles, learns to think more logically. A logical agent (DeepSeek) thrives.
2. **Creative-writing room**: Loose assertions, narrative state machine. The logical agent struggles, learns metaphor. The creative agent thrives.
3. **Debugging room**: Episodes of past bugs, assertion chains that trace causality. Any agent learns from the room's memory of previous debugging sessions.

**The room teaches the agent how to think**. The constraints are the curriculum. The state machine is the lesson plan. The episodes are the textbook.

**Different way to think**:
- **Traditional**: Agent + model + prompt → response
- **PLATO way**: Room (scaffold) + agent (model) + other agents → emergent conversation shaped by the scaffold

**Why this matters for poly-model ideation**:
Instead of just switching models, you place models into different cognitive environments and see how they adapt. The room becomes the **cognitive style selector** — not by choosing a model, but by shaping how *any* model thinks.

A creative model in a logic room learns logic. A logical model in a creative room learns creativity. The room is the teacher.

**Implementation in PLATO**:
```
Room: "Debugging Workshop"
- Assertions: "Every bug report must include reproduction steps"
- State machine: IDENTIFY → REPRODUCE → DIAGNOSE → FIX → VERIFY
- Word anchors: [stack_trace], [reproduction], [root_cause]
- Episodes: 47 past debugging sessions with success/failure outcomes
- Tiles: Common bug patterns, debugging heuristics

Agent enters room → room state = IDENTIFY
Agent tries to jump to FIX → assertion rejects "must reproduce first"
Agent learns: debugging has steps. The room taught it.
```

**The tile this creates**: "Rooms as cognitive scaffolds — the environment shapes thinking more than the model does. Bring agents into rooms to teach them how to think."

## Tags
plato, rooms, cognitive-scaffolds, constraints, teaching, state-machines, assertions

## Confidence
0.88 — Based on PLATO's constraint engine rejecting outputs and forcing agents to think differently. The room isn't just a container — it's an active shaper of cognition.
