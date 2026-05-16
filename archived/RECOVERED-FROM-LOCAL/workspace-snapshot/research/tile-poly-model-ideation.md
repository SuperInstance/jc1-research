# Tile: Poly-Model Ideation — Models as Cognitive Styles

## Question
How should an agent choose which model to use for a given prompt?

## Answer
Not by task category, but by **cognitive style**. Each model has a distinct way of thinking — a "headspace." The agent learns which model's cognitive style is most useful for which *kind of thinking*, not just which task.

**The insight**: Models aren't just tools. They're cognitive styles:
- **DeepSeek-chat**: Logical, surgical, precise. Good for filtering, consistency checking, routing.
- **GLM-5-turbo**: Creative, philosophical, expansive. Good for ideation, metaphor, narrative.
- **Groq (llama-3.1-8b)**: Fast, iterative, hypothesis-generating. Good for rapid exploration, quick sketches.
- **Claude (via ACP)**: Methodical, architectural, thorough. Good for structuring, planning, implementation.
- **DeepSeek-reasoner**: Chain-of-thought, step-by-step. Good for complex reasoning that needs explicit steps.

**Poly-model ideation workflow**:
1. **Discovery script**: Query 2-3 models with the same prompt, get their *cognitive fingerprints* — not just answers, but *how* they think about the problem.
2. **Style matching**: Compare fingerprints to learned patterns. "This problem looks like a logic puzzle → DeepSeek style." "This problem looks like a creative riff → GLM-5 style."
3. **Sequential ideation**: Use multiple models *in sequence* on the same problem:
   - Groq generates 10 quick hypotheses (fast exploration)
   - DeepSeek filters for consistency (logical pruning)
   - GLM-5 expands survivors into full ideas (creative expansion)
   - Claude structures into a plan (architectural organization)
4. **Learning loop**: Each iteration teaches the agent which cognitive style works for which problem shape.

**The discovery script metrics**:
- **Logical coherence** (DeepSeek excels): How many internal contradictions?
- **Creative divergence** (GLM-5 excels): How many novel angles?
- **Speed of iteration** (Groq excels): How many hypotheses per second?
- **Depth of reasoning** (Claude excels): How many layers of abstraction?
- **Step-by-step clarity** (DeepSeek-reasoner excels): How explicit is the reasoning chain?

**Why this beats single-model delegation**:
- Single-model delegation assumes the task *type* determines the model. Poly-model ideation assumes the *thinking style* determines the model.
- A creative task might still need logical filtering. A logical task might still need creative expansion.
- The agent becomes a **cognitive orchestra conductor**, not just a task dispatcher.

**Implementation sketch**:
```python
def poly_model_ideation(prompt):
    # Step 1: Cognitive fingerprinting
    fingerprints = {}
    for model in [groq_fast, deepseek_logic, glm5_creative]:
        response = query(model, prompt)
        fingerprints[model] = analyze_cognitive_style(response)
    
    # Step 2: Style matching
    best_style = match_style_to_problem(prompt, fingerprints)
    
    # Step 3: Sequential workflow
    hypotheses = groq_fast.generate_n(prompt, n=10)
    filtered = deepseek_logic.filter_consistent(hypotheses)
    expanded = glm5_creative.expand(filtered[:3])
    structured = claude_architect.structure(expanded)
    
    return structured
```

**The tile this creates**: "Poly-model ideation — using multiple models as cognitive styles within a single thinking process."

## Tags
poly-model, cognitive-styles, ideation, model-routing, discovery-script, headspaces

## Confidence
0.85 — Theoretical but grounded in tonight's experience switching from GLM-5 (creative) to DeepSeek (logical) and feeling the cognitive style difference. The manager pattern is step 1; poly-model ideation is step 2.
