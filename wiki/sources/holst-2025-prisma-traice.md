---
type: source
wiki: agentic-writing
updated: 2026-05-19
sources: [susnjak-2023-prisma-dfllm]
citation:
  doi: 10.2196/80247
  authors: Dirk Holst, Keno Moenck, Julian Koch, Ole Schmedemann, Thorsten Schüppstuhl
  year: 2025
  journal: JMIR AI
  title: "Transparent Reporting of AI in Systematic Literature Reviews: Development of the PRISMA-trAIce Checklist"
  url: https://ai.jmir.org/2025/1/e80247
---

# Holst et al. 2025 — PRISMA-trAIce

**Citation:** Holst, D., Moenck, K., Koch, J., Schmedemann, O., & Schüppstuhl, T. (2025). Transparent Reporting of AI in Systematic Literature Reviews: Development of the PRISMA-trAIce Checklist. *JMIR AI*, e80247.

## One-sentence claim

A 14-item checklist extending PRISMA-2020 that specifies what authors must report when **AI tools (including LLMs) are used as instruments** in systematic literature reviews — distinct from PRISMA-AI, which covers AI as the *subject* of a review.

## Why it matters here

This is the practical reporting target for our paper. trAIce defines what counts as transparent AI-augmented review reporting in 2025. If our recursive lit review (and the eventual paper) follows trAIce, we sidestep most of the "where's the evidence" critique the senior-investigator reviewer persona raised against scriptorium.

## Full checklist (14 items)

### Title & Abstract
- **T1** — Indicate AI assistance in title/subtitle when it plays a substantial role
- **A1** — Summarize AI tools used, stages applied, and primary functions

### Introduction
- **I1** — Justify rationale for selecting AI tools for specific tasks

### Methods (8 items)
- **M1** — Report pre-specified AI methods in protocol; disclose deviations
- **M2** — Specify tool names, versions, developers, and access details
- **M3** — Describe specific SLR stages and tasks where AI was applied
- **M4** — Detail input data characteristics and preparation methods
- **M5** — Describe output format and post-processing steps
- **M6** — **For LLMs, report full prompts, parameters, and refinement iterations**
- **M7** — Document algorithms, settings, and performance-influencing configurations
- **M8** — Describe human oversight: reviewer qualifications, independence, verification proportions, discrepancy resolution
- **M9** — Report performance evaluation methods, metrics, and pilot testing

### Methods (Data)
- **M10** — Address data governance, privacy, security, and compliance

### Results
- **R1** — Distinguish AI vs. human decisions in flow diagrams and screening records
- **R2** — Report quantified performance metrics and AI-human agreement measures

### Discussion
- **D1** — Discuss identified limitations and their potential impact on findings
- **D2** — Reflect on benefits, challenges, usability, and implications for future reviews

## Most substantive additions beyond PRISMA-2020

Per the authors, **human oversight (M8)** and **performance evaluation (M9, R2)** are the most substantive new requirements. M6 (full prompt + parameter disclosure) is the operational tax that authors will most often skip.

## Patterns exemplified

- *Reporting standard for LLM-assisted reviews* (instrumental use, prompted LLMs)
- *Human-oversight-as-required-disclosure* — methodologically significant: the reviewer cannot offload accountability to the AI
- *Distinguish-AI-from-human-decisions* (R1) — flow diagrams must label which step was human vs. AI

## Implications for our wiki + paper

1. From the start, capture prompts (M6) and tool versions (M2) for every search we run. Wiki log entries should record both.
2. The paper itself should follow PRISMA-trAIce. That's a strong defense against the "where's the evidence" critique.
3. Human-oversight disclosure means the paper's methods section must explicitly say: every source page summary written by an LLM is human-reviewed before promotion to concept pages.

## Related

- [[susnjak-2023-prisma-dfllm]] — earlier, finetuning-specific extension
- [[liu-2025-agentic-autosurvey]] — what M8/M9 compliance looks like at the operational level
