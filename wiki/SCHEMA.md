# Agentic Writing Wiki — Schema

**Domain:** Agentic and LLM-assisted scholarly writing — manuscript drafting, citation handling, reviewer simulation, reference synthesis, format conversion, and the surrounding research workflows that feed those outputs.

**Purpose:** Build an evidence-grounded catalog of design patterns and published tools/systems for agentic scholarly writing. Outputs feed a planned narrative-review / design-patterns paper. The paper's argument is that the field already has evidence behind several distinct patterns; the wiki is where that evidence accumulates.

**Vault root:** `~/Documents/seandavis/`

**Started:** 2026-05-19

---

## Why a separate wiki

`wiki/llm-bio/` covers LLMs and agentic AI in biomedicine broadly. Agentic scholarly writing has its own canonical literature (Manubot, Quarto, ResearchAgent, AutoRA, Elicit, Consensus, scriptorium) that mostly doesn't overlap with biomedical-AI per se. Keeping them separate prevents both wikis from blurring.

---

## Directory Layout

```
raw/agentic-writing/         # Immutable source files (PDFs, markdown clips, papers)
wiki/agentic-writing/        # LLM-maintained wiki (THIS directory)
  SCHEMA.md                  # This file
  index.md                   # Catalog of all wiki pages
  log.md                     # Append-only operation log
  methodology.md             # How we run the lit review for this wiki
  sources/                   # One summary page per ingested paper / preprint
  entities/                  # Named tools, systems, platforms, people, papers
  concepts/                  # Design patterns, frameworks, gaps, recommendations
  comparisons/               # Side-by-side analyses of 2+ entities or patterns
  triage/                    # Phase 1 (title/abstract) AI-generated screening decisions pending human review
```

---

## Page Types

### `source` — Summary of an ingested paper
One page per source. Records citation metadata (DOI/arxiv/PMID — resolvable by quartobot), one-sentence claim, design pattern(s) exemplified, evidence strength, and which wiki pages it informed.

### `entity` — A named thing
Tools (Manubot, Quarto, Elicit), systems (scriptorium, ResearchAgent), papers, labs, datasets, people. Each entity gets its own page.

### `concept` — A design pattern or recommendation
Architectural patterns (deterministic-pipeline + LLM-arbiter, knowledge-layer-as-ground-truth, skills-as-composable-units), reporting requirements (PRISMA-trAIce items), known failure modes (hallucinated citations, screening misses).

### `comparison` — Side-by-side analysis
Used when two patterns or tools are in tension and the comparison clarifies trade-offs.

### `methodology` — `methodology.md` is the working-practice document
How we run *this* lit review. Grounded in PRISMA-trAIce + Agentic AutoSurvey + lessons from the wiki as it grows. Living document; updated as we hit failure modes.

### `triage/` — Phase 1 screening decisions (added 2026-05-20; PRISMA-trAIce M1 deviation disclosure)

Phase 1 (title/abstract sweep) outputs live here, **not** in `sources/`. A triage file records the AI-generated include / exclude / borderline decision for every PMID (or arXiv ID, DOI) in a given search batch, along with the reason. These are decision records — **not** concept pages or source pages. They exist so that:

1. The full R1 audit trail (which AI decisions led to which records being kept vs. dropped) is preserved even for excluded papers, which never get source pages.
2. Human review (Sean) of the Phase 1 decisions happens via PR review on the triage file before Phase 2 (source-page ingestion) begins.
3. The triage step is itself the kind of LLM-as-instrument-in-SR pattern this wiki catalogs, so making it explicit and recorded is consistent with the wiki's own thesis.

Frontmatter for a triage file:

```yaml
---
type: triage
phase: 1
wiki: agentic-writing-patterns
date: YYYY-MM-DD
pmid_count: N
status: awaiting-human-review | human-reviewed | merged
reviewer: Sean Davis (pending | YYYY-MM-DD)
search_date: YYYY-MM-DD
search_source: brief description
metadata_file: relative path to raw metadata
---
```

A triage file is "done" once Sean has reviewed and either signed off or edited the decisions, and the corresponding Phase 2 source pages have been written.

---

## Frontmatter

```yaml
---
type: source|entity|concept|comparison|methodology
wiki: agentic-writing
updated: YYYY-MM-DD
sources: [source-slug-1, source-slug-2]
citation:
  doi: 10.xxxx/yyy
  arxiv: 2306.14905
  pmid: 12345678
---
```

The `citation` block is optional and only on `source` pages. Other pages list source-slug references in `sources:`.

---

## Ingest Workflow

When asked to ingest a source:

1. **Read** the raw file (or fetch via DOI/PMID/arxiv if needed — quartobot resolves these)
2. **Triage** — does this paper actually exemplify a pattern relevant to the catalog, or is it field-adjacent? Skip field-adjacent.
3. **Write source summary** to `sources/[slug].md` with citation metadata, key claims, pattern(s) exemplified, evidence strength.
4. **Update entity pages** for any tool/system named.
5. **Update concept pages** — promote a pattern to a concept page once 3+ sources support it. Before then, mention in sources only.
6. **Update `methodology.md`** if the source surfaces a new failure mode or best practice for the lit review process.
7. **Update `index.md`** — add new pages.
8. **Append to `log.md`** — `## [YYYY-MM-DD] ingest | [Source title]` + bullet summary.

---

## Query Workflow

Same as `llm-bio`: read `index.md`, drill into relevant pages, synthesize, cite with `[[wiki-links]]`. If a query produces novel synthesis, file it as a concept or comparison page.

---

## Lint Workflow

Same as `llm-bio`, plus one addition specific to this wiki:

- **Pattern-evidence audit:** every concept page must list ≥3 sources or be marked `status: provisional`. Single-source patterns are claims, not patterns.

---

## Methodology Discipline

This wiki documents work that will become a published review. That means:

- **Citation traceability is non-negotiable.** Every claim on a concept page must trace to a source page, which must trace to a real DOI/arxiv/PMID.
- **PRISMA-trAIce compliance is the target** for the eventual paper. The wiki captures what trAIce will require us to report: tool versions, prompts, screening decisions, AI-vs-human verifications, performance evaluation.
- **Living document, not a finished product.** Pages get rewritten as patterns clarify.

See `methodology.md` for the operational version of this discipline.

---

## Wiki-Link Convention

Same as `llm-bio`. `[[page-slug]]` resolves in order: `entities/`, `concepts/`, `sources/`, `comparisons/`. Cross-vault links: `[[some-note]]` (notes), `[[some-decision]]` (decisions).

---

## Log Format

```
## [YYYY-MM-DD] <operation> | <title>
- Key finding or action
- Pages created: [...]
- Pages updated: [...]
```

Operations: `ingest`, `query`, `lint`, `update`, `bootstrap`.
