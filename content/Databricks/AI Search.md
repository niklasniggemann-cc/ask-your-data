---
title: AI Search
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Vector & Retrieval Search
tags:
  - databricks
  - retrieval
---

## Definition

AI Search is Databricks' fully managed retrieval product for agent and RAG pipelines — formerly branded **Vector Search** (Python SDK renamed from `databricks-vectorsearch` to `databricks-ai-search`). It handles ingestion, embedding, indexing, reranking, and quality tuning out of the box, in contrast to [[Lakebase Search]], which is a lower-level, Postgres-native search primitive for teams that want retrieval running directly alongside their operational data.

## Core Capabilities

- **Managed indexing pipeline** — ingestion, embedding, and reranking handled automatically, with built-in retrieval quality evaluation for comparing search strategies
- **Storage Optimized endpoints** — deployment option for billion-scale vector indexes that decouples storage (cloud object storage) from compute; builds billion-vector indexes in under 8 hours (~20x faster than Standard endpoints), at up to 7x lower serving cost, using an IVF + Product Quantization architecture with a Rust query engine. Trade-off: ~300–500ms query latency vs. 20–50ms on Standard endpoints
- **Dedicated full-text search index** (Beta) — a Delta Sync Index created with no embedding columns at all, for keyword-only BM25 search; storage-optimized endpoints only, triggered sync mode. Distinct from the hybrid vector+keyword search already available on standard vector indexes — this option skips embeddings entirely for pure keyword/identifier lookups
- **`ai_prep_search`** — SQL function (Beta) that transforms `ai_parse_document` output into search-ready chunks for RAG pipelines

## AI Search vs. Lakebase Search

Databricks now offers two distinct retrieval products:

- **AI Search** — best fit for teams that want a fully managed retrieval service with ingestion/embedding/reranking handled for them
- **[[Lakebase Search]]** — best fit for agent workloads that want search running as a native, transactional part of their Postgres-backed operational data (Lakebase), with tighter read/write latency for agent memory loops

## Recent Developments

- **2026-09-08** — **`ai_search` supports citations**: a new `generate_citations` option (requires `generate_answer: true`) returns which retrieved chunks the model used to support its generated answer, as an array of `document_index` positions into the returned `document` array. Indices are only valid within a single response — they can shift between calls, reranking changes, or index updates. Databricks frames these as the model's best-effort picks of supporting evidence, not proof of any specific claim. Extends the same grounded-answer pipeline already used by `ai_search` with a lightweight attribution layer, useful for building trust in agent/RAG answers that cite this function. [Source](https://docs.databricks.com/aws/en/sql/language-manual/functions/ai_search)
- **2026-09-09** — **Adaptive Instructed-Retriever**: a new small, specialized retrieval model extending Databricks' earlier Instructed-Retriever-1 (parallel single-step search) with adaptive multi-step sequential search — the agent decides per-query how many search steps are worth the added latency, stopping early on simple lookups and continuing on harder multi-hop questions, up to a fixed step limit. Trained with online reinforcement learning (CISPO) that rewards high-performing search trajectories while penalizing steps that don't improve results; sweeping the step-penalty weight during training produces a family of checkpoints along a quality-latency frontier, so a workload can pick the tradeoff it needs. Matches the retrieval quality of Claude Sonnet 5, GPT-5.6 Luna, and DeepSeek-V4-Flash at roughly 2x lower latency (5.8s vs. their multi-step responses) across a mix of internal/external benchmarks. Framed explicitly as the retrieval building block underneath Genie Code, Genie One, and Genie Agents, which all need to find the right tables/notebooks/dashboards/documents in a large, changing workspace without over-searching. [Source](https://www.databricks.com/blog/adaptive-instructed-retriever-frontier-quality-search-2x-lower-latency)
- **2026-09-02** — **Struct and map column support, plus filter-only queries**: indexes can now index and filter on struct and map columns (e.g. `filters={"profile.age": 18, "attrs['voltage']": 9}`), and support filter-only queries that return rows matching a filter with no vector or keyword retrieval. Arrays/maps can't nest inside structs; maps must be top-level with string keys and primitive values. [Source](https://docs.databricks.com/aws/en/ai-search/query-ai-search)
- **2026-08-27** — **Structured chart-JSON extraction for `ai_parse_document`** (research, not yet shipped — "available soon"): a new enrichment extracts charts as structured JSON (values, labels, series) instead of just an image caption, paired with `ai_prep_search` chunking and a lightweight 300M-parameter text embedding model for indexing via `ai_search`. Across two chart-heavy benchmarks (ViDoRe V3 subset, and a synthetic "Chart-RAG" set from BIS/IMF/J.P. Morgan reports), it improved both retrieval and answer correctness, and — paired with the top 3 retrieved images — beat four multimodal embedding baselines (including ColQwen2.5-3B) on answer quality at ~10x smaller model size and lower cost. No interface changes required; will power [[Genie One]]'s answers to chart-related questions over PDFs. [Source](https://www.databricks.com/blog/enhancing-agent-retrieval-structured-chart-extraction)
- **2026-08-25** — **`ai_prep_search` accepts plain text and markdown input** (Beta): previously required the structured `VARIANT` output of `ai_parse_document`; now also takes plain-text/markdown `STRING` content directly, so text you already have as a string can be chunked for indexing and RAG without a document-parsing step first. [Source](https://docs.databricks.com/aws/en/sql/language-manual/functions/ai_prep_search)
- **2026-08-09** — Databricks published the `ai_search()` SQL function (Beta, released Aug 7). Given a natural-language query and up to 10 AI Search indexes as knowledge sources, it generates optimized search queries, retrieves/dedupes/reranks results, and by default synthesizes a grounded natural-language answer from the retrieved documents — usable directly in SQL for batch RAG pipelines or as a retrieval tool inside a compound AI system. Complements `ai_prep_search` (chunking): `ai_parse_document` → `ai_prep_search` → index → `ai_search` now covers the full pipeline. [Source](https://docs.databricks.com/aws/en/sql/language-manual/functions/ai_search)

## Related

- [[RAG]] — the primary use case AI Search enables: retrieval-augmented generation over managed indexes
- [[Databricks]] — parent platform
- [[Lakebase Search]] — Postgres-native alternative for agent-first retrieval
- [[Unity Catalog]] — governs access to AI Search indexes like any other data asset
