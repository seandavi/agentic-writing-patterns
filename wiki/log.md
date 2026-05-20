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

## [2026-05-20] Phase 1 triage — 25 PMIDs (2026-05-19 search)

Phase 1 (title/abstract sweep) triage of the 25 PubMed PMIDs queued in the 2026-05-19 ingest session above. **AI-generated output; pending human review per PRISMA-trAIce M8.** Source pages (Phase 2) will be written only after Sean signs off on the triage decisions via PR review.

### Tools used (PRISMA-trAIce M2, M3)

- **Metadata retrieval:** NCBI E-utilities (esummary, efetch) via `curl` + `bash` shell script. Polite delay 0.4s between calls (≤2 req/sec). One PMID (40332983) returned a 500 on first efetch and was successfully retried after a 2s back-off.
- **Triage model:** Claude (Anthropic) Opus 4.7 via Claude Code; model id `claude-opus-4-7`, knowledge cutoff January 2026. Single pass; no iterative refinement.
- **Stage:** Phase 1 title/abstract sweep (`methodology.md` principle 2). Phase 2 (source-page ingest) deferred to post-human-review.

### Inputs (PRISMA-trAIce M4)

- 25 PMIDs from the 2026-05-19 PubMed search (full query in the prior log section).
- For each PMID: title, authors, year, journal, DOI, publication type, and full PubMed abstract text. Consolidated to `wiki/raw/pubmed-methodology-2026-05-19-metadata.json`.

### Triage prompt (PRISMA-trAIce M6)

The triage prompt was the task description issued by Sean to a Claude Code sub-agent on 2026-05-20. The full instructions are preserved in the conversation transcript; the operational core, paraphrased for the methodology trail:

> For each PMID, read title + abstract. Apply scope rules from `README.md`: **include** if the paper describes a design pattern, tool, system, methodology, or evidence about agentic AI / LLM-assisted scholarly writing covering any pipeline stage (topical research, gap analysis, drafting, citation handling, synthesis, revision, reviewer simulation, format conversion). **Exclude** if (a) general LLM benchmarks unrelated to scholarly writing, (b) non-scholarly writing tools, (c) finetuned-LLM-specific workflows with no broader pattern relevance, (d) LLMs as the *subject* of a review (PRISMA-AI territory) rather than as an *instrument* in producing one, (e) pure prompt-engineering tutorials with no writing context. **Borderline** (flag, don't decide unilaterally): domain-specific reviews that use LLMs without explicit pattern discussion. Write a 1-2 sentence reason per decision; note candidate pattern(s) for includes.

No iterations or refinements: this is a single AI pass. Human review on the PR is the verification step.

### Output (PRISMA-trAIce M5, R1)

- Triage decisions: `wiki/triage/phase-1-pmid-2026-05-19.md`
- Decisions summary: 3 include / 19 exclude / 3 borderline (of 25 PMIDs scanned).
- Includes: PMIDs 40021099 (Lieberum 2025 — LLMs for conducting SRs scoping review), 38214966 (Guo 2024 — automated paper screening with GPT-4), 40332983 (Scherbakov 2025 — LLM-assisted SR of LLMs in literature reviews).
- Borderlines: PMIDs 39903463 (CHART reporting tool), 38462064 (ChatGPT medical-response evaluation framework), 39812777 (RAG-LLM SR with development guidelines).

### Human oversight (PRISMA-trAIce M8)

This is the AI-decided layer of the screening record. Sean Davis is the human reviewer; sign-off happens via PR review (`triage/phase-1-pmid-2026-05-19`) before Phase 2 source-page ingestion begins. The R1 flow-diagram requirement is satisfied by recording every PMID's decision in the triage file with its reason, regardless of include/exclude outcome.

### M8 disclosure

This Phase 1 triage output was generated by Claude (Opus 4.7) operating as a sub-agent under direction from Sean Davis. The decisions are AI-generated and explicitly marked `status: awaiting-human-review` in the triage page frontmatter. No source page is written and no concept page is promoted until the human reviewer signs off via PR review.

Pages created: [triage/phase-1-pmid-2026-05-19.md, raw/pubmed-methodology-2026-05-19-metadata.json]
Pages updated: [log.md, SCHEMA.md (added `triage/` directory entry)]
