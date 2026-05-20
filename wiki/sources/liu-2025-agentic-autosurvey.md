---
type: source
wiki: agentic-writing
updated: 2026-05-19
sources: []
citation:
  arxiv: 2509.18661
  authors: Yixin Liu, Yonghui Wu, Denghui Zhang, Lichao Sun
  year: 2025
  title: "Agentic AutoSurvey: Let LLMs Survey LLMs"
---

# Liu et al. 2025 — Agentic AutoSurvey

**Citation:** Liu, Y., Wu, Y., Zhang, D., & Sun, L. (2025). Agentic AutoSurvey: Let LLMs Survey LLMs. arXiv:2509.18661.

## One-sentence claim

A **four-agent multi-agent architecture** for automated literature surveys outperforms single-agent baselines (8.18/10 vs. 4.77/10) and scales to 75–443 papers per topic, with citation coverage often ≥80% on 75–100-paper sets.

## Why it matters here

This is the **operational counterpart** to the reporting standards in [[holst-2025-prisma-traice]] — i.e., if you're going to build a system that does what trAIce requires you to document, here's what one such system actually looks like. Also names the failure modes that surface at scale.

## Architecture (four agents)

1. **Paper Search Specialist** — locates relevant publications
2. **Topic Mining & Clustering** — organizes papers thematically
3. **Academic Survey Writer** — synthesizes content into survey form
4. **Quality Evaluator** — assesses output quality

Agents work collaboratively through an orchestrated pipeline. The Quality Evaluator gating step is the architectural feature most aligned with the [[llm-arbiter-with-deterministic-seed]] pattern Sean has built elsewhere.

## Evaluation methodology

- **12-dimension evaluation framework** extending beyond standard text-quality metrics to include organization, synthesis integration, and critical analysis capabilities
- Tested on six LLM research topics from COLM 2024
- 847 papers total processed across topics

## Results

- 8.18/10 vs. AutoSurvey's 4.77/10 on the 12-dim eval
- ≥80% citation coverage on 75–100-paper sets
- Reduced performance on very large sets (e.g., RLHF) — scalability ceiling

## Failure modes named

- **Scalability ceiling** at "very large" paper sets — exact threshold not given, but RLHF was cited as a domain where the system underperforms. Suggests the four-agent shape works for tractable topic-sized surveys but not whole-field reviews.
- Implicit: the paper does not address citation hallucination directly. Worth checking the full PDF for whether the Quality Evaluator catches fabricated citations or only assesses prose quality.

## Patterns exemplified

- *Multi-agent specialization* — distinct agents for search, clustering, writing, evaluation
- *Quality-gate-as-arbiter* — final agent verifies output, mirroring [[llm-arbiter-with-deterministic-seed]]
- *Operationalization of human-oversight requirements* — Quality Evaluator role is the closest LLM analog to PRISMA-trAIce's M8 human-oversight requirement, though it's still LLM, not human

## Open questions for our paper

1. How does the four-agent shape compare to single-agent + tool-calling? (Same outcomes with less orchestration overhead?)
2. Does the Quality Evaluator detect hallucinated citations, or only assess prose?
3. What's the cost (token spend) per surveyed topic? Not disclosed in abstract.

## Related

- [[holst-2025-prisma-traice]] — reporting standard this architecture would be evaluated against
- [[susnjak-2023-prisma-dfllm]] — earlier, finetuning-based alternative architecture
- [[llm-arbiter-with-deterministic-seed]] — Sean's own framing of the Quality-Gate pattern
