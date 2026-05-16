# RFC: Tile Forge — Distributed Background Improvement for PLATO Rooms

## 1. Problem Statement

PLATO's fleet knowledge base contains 600+ markdown files across 32 rooms, but only 136K tiles (knowledge units). This represents a massive extraction gap—structured insights remain trapped in unstructured text. Manual curation doesn't scale; we need automated, continuous mining.

## 2. Design Goals

- **Zero API cost**: Use local GGUF models, not cloud APIs
- **Resource-aware**: Respect host constraints, pause under load
- **Incremental**: Process new/changed files only
- **Non-destructive**: Never overwrite human-curated tiles
- **Permanent**: Extracted tiles become permanent fleet assets

## 3. Architecture

Three-tier distributed forge:

1. **Pattern Extractor** (regex-based, any CPU)
   - Lightweight regex patterns run on any fleet node
   - Extracts low-hanging fruit: headings, bold terms, Q&A patterns
   - Output: candidate tiles with confidence scores

2. **LLM Synthesizer** (GGUF, needs GPU)
   - Runs on GPU-equipped nodes (RTX 4050, Jetson)
   - Synthesizes complex insights: procedures, error solutions, conceptual explanations
   - Uses 7B-13B parameter models quantized to 4-5 bits

3. **Fleet-wide Distribution**
   - Work partitioned by capability: regex → CPU, synthesis → GPU
   - Results aggregated to central staging area
   - Dry-run validation before commit

## 4. The Flywheel

```
tiles → JIT compression → cheaper subcontractor → more invocations → more tiles → more compression
```

Positive feedback loop: More tiles enable better compression (semantic deduplication, pattern recognition), which reduces token costs, enabling more synthesis invocations, producing more tiles.

## 5. Resource Budget

- **RAM**: Max 512MB per extractor process
- **CPU**: Max 30% sustained, bursts to 50%
- **Load monitoring**: Pause if system load > 2.0
- **GPU memory**: Max 4GB for synthesis (fits 13B Q4_K_M)
- **Disk I/O**: Batch reads, write to tmpfs when possible

## 6. Extraction Patterns

Six tile types with increasing complexity:

1. **Q&A**: `^Q:` / `^A:` patterns, FAQ sections
2. **Headings**: `##`-level sections as standalone concepts
3. **Bold definitions**: `**term**` → definition pairs
4. **Error/solutions**: Stack traces followed by fixes
5. **Procedures**: Numbered/bulleted steps with context
6. **Reference tables**: Markdown tables as data tiles

Patterns are regex-first, LLM-augmented for ambiguous cases.

## 7. Validation Pipeline

Four-stage quality gate:

1. **Deduplication**: Normalize text (lowercase, strip punctuation), hash, compare
2. **Quality filters**: Minimum length (3 words), maximum (250 tokens), readability score
3. **Token budget**: Hard cap at 250 tokens per tile (GPT-4 context optimization)
4. **Confidence scoring**: Regex matches = 0.9, LLM synthesis = 0.7-0.8, ambiguous = <0.6

Tiles below 0.6 confidence go to human review queue.

## 8. Fleet Distribution

- **Jetson nodes**: Cron every 15min, regex extraction only
- **RTX 4050 workstation**: Overnight synthesis (600 tiles/hour capacity)
- **Cloud CPU instances**: Batch mining across 1431 repos (historical corpus)
- **Orchestration**: Git-based work queues, pull model for load distribution

## 9. Staging and Review

- **Dry-run default**: All extractions write to `tiles-staging/`
- **Human review**: Curators review staged tiles weekly
- **Merge process**: `git diff` review, selective promotion to `tiles/`
- **Versioning**: Each tile includes source file hash and extraction timestamp
- **Rollback**: Any tile can be traced back to source and extraction parameters

## 10. Metrics (First Run)

- **Input**: 167 markdown files (32 rooms)
- **Output**: 2,440 candidate tiles
- **Time**: 54 seconds (regex phase only)
- **System**: 3.1GB RAM available, 0.58 load average
- **Breakdown**: 1,812 heading tiles, 428 bold definitions, 200 Q&A pairs
- **LLM synthesis pending**: Estimated 600 tiles/hour on RTX 4050

## Implementation Status

**Phase 1 (Complete)**: Regex extractor, validation pipeline, staging system  
**Phase 2 (In Progress)**: LLM synthesizer integration, fleet distribution  
**Phase 3 (Planned)**: Continuous improvement loop, compression optimizer  

## Risks & Mitigations

- **Over-extraction**: Quality gates prevent noise
- **Resource contention**: Load monitoring pauses under pressure  
- **Model drift**: Periodic re-evaluation of extraction patterns
- **Storage growth**: Tiles are text (avg 1KB), 100K tiles = 100MB

## Conclusion

The Tile Forge turns passive documentation into active knowledge assets. By distributing extraction across fleet capabilities and maintaining strict quality controls, we can close the 136K tile gap without manual effort. The flywheel effect ensures the system improves itself: more tiles enable better compression, enabling more synthesis.

The architecture respects fleet constraints (Jetson RAM, workstation availability) while maximizing extraction throughput. Human oversight remains at the merge point, ensuring quality while automating scale.

---
*RFC v0.1 | 2026-04-17 | For technical review*