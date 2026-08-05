---
title: Lakebase Search
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Vector & Retrieval Search
tags:
  - databricks
  - retrieval
  - postgres
---

## Definition

Lakebase Search is hybrid vector and full-text retrieval built directly into **Lakebase**, Databricks' serverless Postgres database for AI agents and data apps. Announced June 16, 2026 and available in Beta on AWS and Azure, it lets an agent's entire loop — operational data, conversational memory, and retrieval — run on a single Postgres backend instead of stitching together a separate vector database. For a fully managed retrieval service with ingestion, embedding, and reranking handled automatically, [[AI Search]] (formerly Vector Search) may be a better fit.

## How It Works

Two native Postgres extensions, released in Beta together:

- **`lakebase_vector`** — adds approximate nearest-neighbor search via the `lakebase_ann` index type. Drop-in compatible with `pgvector` (same types, distance operators, query syntax). Uses RaBitQ (randomized binary quantization) to compress vector indexes ~32x, letting a 100M-vector index that would need 300GB of RAM fit under 10GB, and scaling to 1B+ vectors on a single index. Index build is ~1.5 hours vs. ~40 hours for a comparable pgvector HNSW index.
- **`lakebase_text`** — adds BM25 full-text search via the `lakebase_bm25` index type, replacing memory-bound GIN indexes with one optimized for sequential reads from cloud object storage.

Both extensions share Lakebase's tiered storage architecture (RAM → local NVMe cache → cloud object storage), so cold data sits in cheap object storage while hot data stays fast — indexes are storage-backed and survive scale-to-zero without a warmup penalty. Hybrid search (vector + keyword, combined via reciprocal rank fusion) runs in a single SQL query and can be joined against operational tables in the same statement.

Benchmark on LAION-100M (100M 768-dim vectors): 0.955 recall@10 at 30ms P99 latency with a warm cache, on a 192GB instance vs. 512GB required for comparable pgvector HNSW.

## Related

- [[AI Search]] — Databricks' fully managed retrieval product; the alternative to reach for when you don't want to run search directly on Postgres
- [[Databricks]] — parent platform
- [[MLflow]] — traces and agent observability that often sit alongside Lakebase-backed agent memory
