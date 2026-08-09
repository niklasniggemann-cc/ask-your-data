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

- **2026-08-09** — Databricks published the `ai_search()` SQL function (Beta, released Aug 7). Given a natural-language query and up to 10 AI Search indexes as knowledge sources, it generates optimized search queries, retrieves/dedupes/reranks results, and by default synthesizes a grounded natural-language answer from the retrieved documents — usable directly in SQL for batch RAG pipelines or as a retrieval tool inside a compound AI system. Complements `ai_prep_search` (chunking): `ai_parse_document` → `ai_prep_search` → index → `ai_search` now covers the full pipeline. [Source](https://docs.databricks.com/aws/en/sql/language-manual/functions/ai_search)

## Related

- [[RAG]] — the primary use case AI Search enables: retrieval-augmented generation over managed indexes
- [[Databricks]] — parent platform
- [[Lakebase Search]] — Postgres-native alternative for agent-first retrieval
- [[Unity Catalog]] — governs access to AI Search indexes like any other data asset
