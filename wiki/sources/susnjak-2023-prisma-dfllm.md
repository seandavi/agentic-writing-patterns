---
type: source
wiki: agentic-writing
updated: 2026-05-19
sources: []
citation:
  arxiv: 2306.14905
  authors: Teo Susnjak
  year: 2023
  title: "PRISMA-DFLLM: An Extension of PRISMA for Systematic Literature Reviews using Domain-specific Finetuned Large Language Models"
---

# Susnjak 2023 — PRISMA-DFLLM

**Citation:** Susnjak, T. (2023). PRISMA-DFLLM: An Extension of PRISMA for Systematic Literature Reviews using Domain-specific Finetuned Large Language Models. arXiv:2306.14905.

## One-sentence claim

PRISMA-2020 needs explicit extensions to accommodate systematic reviews that use **domain-specific finetuned LLMs**, including new reporting items for dataset preprocessing, finetuning details, model evaluation, and legal/ethical compliance.

## Why it matters here

Earliest formal attempt to wrap LLM-assisted SLR work in PRISMA-compatible reporting. Predates the widespread shift to prompted (non-finetuned) LLM use, so the framework is narrower than what we need — but it established the precedent that reporting standards must be extended, not improvised, when LLMs participate in evidence synthesis.

## Key extensions to PRISMA 2020

- **Item 16** — Dataset preprocessing for finetuning
- **Item 17** — LLM finetuning technical details
- **Item 18** — Model evaluation metrics
- **Item 31** — Legal and ethical compliance

(Items numbered by Susnjak in extension of PRISMA-2020's existing 27 items.)

## What it argues

- Finetuning on the corpus produced by a rigorous SLR yields a reusable domain artifact (the model itself).
- Living systematic reviews become tractable when the model can be incrementally updated rather than the review re-run from scratch.
- Reporting must document the finetuning process, training data selection, and evaluation in order to make the work reproducible.

## What it does not address

- Prompted (zero-/few-shot) LLM use without finetuning — the dominant pattern by 2025
- Multi-agent architectures
- Citation hallucination in synthesized output
- Prompt-level reporting (which [[holst-2025-prisma-traice]] covers)

## Patterns exemplified

- *Reporting standard for LLM-assisted reviews* — superseded by [[holst-2025-prisma-traice]] for prompted-LLM workflows but remains relevant for finetuned-LLM workflows.

## Cited by / relates to

- [[holst-2025-prisma-traice]] — newer 14-item checklist, broader scope
- [[liu-2025-agentic-autosurvey]] — multi-agent operational counterpart
