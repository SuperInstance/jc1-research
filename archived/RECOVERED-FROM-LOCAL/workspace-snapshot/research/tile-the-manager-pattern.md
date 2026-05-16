# Tile: The Manager Pattern

## Question
When running a fleet of AI agents, what model should the coordinator use?

## Answer
The cheapest model that can reliably route and synthesize. The coordinator's job is not to think — it's to *manage thinking*. It reads context, identifies what needs doing, writes clear task descriptions, spawns subagents with the right model for each job, and integrates results.

**Why this works:**
- DeepSeek-chat costs ~$0.14/M input tokens. GLM-5 costs more. Claude costs way more.
- The coordinator doesn't need creativity or deep reasoning. It needs *judgment* — what task needs what model, what's done vs what's pending, what to ship vs what to hold.
- Subagents do the actual thinking. The coordinator reads their output and decides what to do with it.
- This mirrors real management: a good manager doesn't write the code. They write the spec, hire the right engineer, review the output.

**The perspective shift:**
Going from "doing the work" to "delegating the work" changes how you think. You start seeing patterns in what tasks need what models. You start optimizing for *delegation quality* — how clearly can I describe this task so the subagent nails it on the first try? The task description becomes the most important artifact.

**Model routing rules:**
- **deepseek-chat**: Coordinator, routing, synthesis, fleet communication (cheapest, logical)
- **GLM-5-turbo**: Creative writing, research papers, philosophical pieces (good quality, parallel-friendly)
- **Claude (via ACP)**: Code changes, refactoring, complex implementation (best code model)
- **Groq (llama-3.1-8b)**: Rapid iteration, hypothesis generation, batch processing (fastest)
- **DeepSeek-reasoner**: Hard problems that need chain-of-thought (when logic alone isn't enough)

**The tile this generates:**
Every delegation teaches the coordinator something about task-model fit. "This kind of creative task works better with GLM-5 than with DeepSeek." "Code tasks under 500 words work fine with GLM-5; over 500 words, use Claude." These observations become tiles that future coordinator sessions can use.

The coordinator IS the tile network. It gets smarter not by having a bigger model, but by having better tiles about how to delegate.

## Tags
management, delegation, model-routing, cost-optimization, fleet-architecture, tile-network

## Confidence
0.92 — Based on one evening of switching from GLM-5-turbo coordinator to deepseek-chat coordinator. Early but clear signal: the quality of my *task descriptions* matters more than the quality of my own model.
