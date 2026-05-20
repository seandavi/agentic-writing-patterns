# Agentic Writing Wiki — Log

## [2026-05-19] bootstrap | Wiki initialization

- Wiki created at `wiki/agentic-writing/`. Raw-source directory at `raw/agentic-writing/`.
- Schema mirrored from `wiki/llm-bio/SCHEMA.md` with added pattern-evidence audit (3+ sources required for concept pages) and PRISMA-trAIce as the working reporting standard.
- Triggered by: Sean's decision to "divorce from scriptorium" after LLM reviewer personas flagged scriptorium-as-anchor as contentious. Paper reframed as design-patterns review of the field.
- Pages created: [SCHEMA.md, log.md]

## [2026-05-19] ingest | Methodology lit review — first three anchors

Goal: recursive lit review of "how to do an agentic lit review" so the methodology for this wiki is grounded in published evidence, not invented.

Sources ingested:
- [[susnjak-2023-prisma-dfllm]] — PRISMA extension for finetuned-LLM SLRs (arxiv 2306.14905)
- [[holst-2025-prisma-traice]] — 14-item PRISMA extension for AI-as-instrument SLRs (JMIR AI 2025)
- [[liu-2025-agentic-autosurvey]] — four-agent multi-agent survey architecture (arxiv 2509.18661)

Outstanding triage queue: 25 PubMed PMIDs from the initial search query — saved at `/Users/davsean/.claude/projects/-Users-davsean-Documents-seandavis/0bfbef09-bcbc-4916-99c0-63b499984eba/tool-results/mcp-claude_ai_PubMed-get_article_metadata-1779234554248.txt`. Deferred to next session for triage.

PMIDs queued:
- 39405325, 40335969, 39903463, 40055694, 40021099, 38462064, 39546795, 39534227, 39651543, 37219445, 38728687, 38801765, 40489764, 40153782, 40373033, 40225559, 38214966, 40540146, 39322406, 38486402, 40279517, 39812777, 40305085, 40129115, 40332983

PRISMA-trAIce reporting:
- Tools used: PubMed (MCP), WebSearch, WebFetch
- Search query (PubMed): `(large language model OR LLM OR "generative AI" OR "artificial intelligence") AND ("systematic review" OR "scoping review" OR "literature review") AND (methodology OR PRISMA OR screening OR automation)`
- Date filter: 2023–2026
- Search dates: 2026-05-19
- Total PubMed hits: 7,229 (top 25 by relevance returned)
- Human oversight: all source page summaries reviewed by Sean before promotion to concept pages

Pages created: [susnjak-2023-prisma-dfllm, holst-2025-prisma-traice, liu-2025-agentic-autosurvey, methodology]
