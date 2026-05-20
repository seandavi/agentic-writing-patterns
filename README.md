# agentic-writing-patterns

A design-patterns review of agentic AI in scholarly writing — catalog, evidence base, and methodology.

This repo is both the working environment for a narrative review paper and the methodology evidence the paper will cite. The wiki is the synthesis layer; issues track decisions and progress; the eventual manuscript will live in `paper/`.

---

## Scope

**In scope**
- Design patterns for AI-assisted scholarly writing in the prompted-LLM era (2023+)
- Patterns identified across the writing pipeline: topical research, gap analysis, drafting, citation handling, revision, reviewer simulation
- Patterns extracted from published, citable sources (DOI / arXiv / PMID resolvable)

**Out of scope**
- General LLM benchmarks unrelated to scholarly writing
- Non-scholarly writing tools (creative, journalistic, marketing)
- Finetuned-LLM workflows (largely superseded by prompted-model approaches; see [Susnjak 2023](wiki/sources/susnjak-2023-prisma-dfllm.md))
- Implementation of the patterns (see [scriptorium](https://github.com/seandavi/scriptorium) for one downstream instance, scoped to manuscript-stage review)

---

## Methodology

PRISMA-trAIce-compliant systematic review ([Holst et al. 2025](wiki/sources/holst-2025-prisma-traice.md)). Full protocol in [`wiki/methodology.md`](wiki/methodology.md).

Operational anchors:
- **Search transparency** — every query, tool version, and date logged in `wiki/log.md`
- **Two-phase triage** — title/abstract sweep, then full-source ingest
- **Pattern-evidence threshold** — concept pages require ≥3 sources before promotion from `provisional`
- **Human-as-Quality-Gate** — Sean reviews every source-page summary before it informs a concept page

---

## Authorship and AI collaboration

This work uses Claude (Anthropic) as a research and writing collaborator under continuous human supervision.

- **Sean Davis** — senior author and intellectual director. Sets scope, makes judgment calls on what counts as a pattern, gates concept-page promotion, approves all synthesis claims. The intellectual responsibility for this work is human.
- **Claude (Anthropic)** — literature retrieval, summarization, drafting, synthesis under direction. Writes prose; does not decide what is true. Functions as a postdoc-equivalent collaborator — capable of substantive technical work, but operating under a senior researcher's direction and accountability.

This division is explicit because it is the paper's own subject matter. Hiding the collaboration would be inconsistent with the work's thesis.

PRISMA-trAIce items M8 (human oversight), R1 (AI-vs-human decision flow), and R2 (AI-human agreement) are satisfied operationally and reported transparently. Prompt templates are documented in [`wiki/prompts.md`](wiki/prompts.md) (created when first template emerges); iteration logs are kept locally and available on request.

---

## Repo structure

```
agentic-writing-patterns/
├── README.md                  this file
├── wiki/                      lit review knowledge base
│   ├── SCHEMA.md              wiki conventions
│   ├── index.md               catalog of all pages
│   ├── log.md                 search history (PRISMA-trAIce M1–M3, M6)
│   ├── methodology.md         operating protocol
│   ├── sources/               one page per ingested source
│   ├── entities/              tools and systems (Manubot, Quarto, etc.)
│   ├── concepts/              named patterns (≥3 sources required)
│   ├── comparisons/           side-by-side analysis pages
│   └── raw/                   primary source files (PDFs, etc.; gitignored where licensing requires)
└── paper/                     manuscript (added when drafting begins)
```

---

## Status

- **2026-05-19** — Wiki bootstrapped. Three anchor sources ingested ([Holst 2025](wiki/sources/holst-2025-prisma-traice.md), [Susnjak 2023](wiki/sources/susnjak-2023-prisma-dfllm.md), [Liu 2025](wiki/sources/liu-2025-agentic-autosurvey.md)). 25 PubMed PMIDs queued for triage. Methodology protocol drafted.
- **2026-05-20** — Repo created. Wiki migrated from private vault. Issues opened for next-phase work.

Target venue: *Patterns* (Cell Press) or similar narrative-review outlet.

---

## How to follow along

- **Open questions and decisions** — see [Issues](../../issues)
- **Synthesis state** — start with [`wiki/index.md`](wiki/index.md)
- **What's been done and what's next** — see Issues + the bottom of [`wiki/log.md`](wiki/log.md)

---

## License

To be determined. Code (if any) likely MIT; prose and synthesis pages likely CC-BY.
