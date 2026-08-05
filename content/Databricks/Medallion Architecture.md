---
title: Medallion Architecture
type:
  - "[[Concept]]"
  - "[[Architecture]]"
context: Data Engineering, Databricks
tags:
  - databricks
---

## Definition

The Medallion Architecture is a data design pattern that organizes data into three progressively refined layers — Bronze, Silver, and Gold — each representing a higher level of data quality and analytical readiness. It is the primary pattern for ensuring [[Data Quality]] reaches the AI analytics layer.

## Layers

| Layer | Contents | Purpose |
|-------|----------|---------|
| **Bronze** | Raw data from sources + metadata | Discovery, lineage, auditability |
| **Silver** | Cleaned, deduplicated, schema-enforced | Single source of truth; most cleaning happens here |
| **Gold** | Refined, aggregated, business-ready | Reporting and AI tools |

### Bronze

- Holds raw ingested data with minimal transformation
- Augmented with metadata for discovery (ingestion timestamps, source file lineage)
- Preserves the full history — no data is discarded

### Silver

- Where most data cleaning happens
- Deduplication via MERGE operations (upserts) or ranking window functions
- Schema enforcement — invalid records blocked, quarantined, or flagged
- Creates a single source of truth across source systems

### Gold

- Aggregated, enriched, and domain-specific views
- Ready for BI tools, dashboards, and AI interfaces
- [[Genie Agents]] should connect to Gold layer tables whenever possible

## Why It Matters for AI

AI tools like [[Genie Agents]] query what they're given. Connecting to Bronze or Silver tables means querying partially cleaned data — the model will present uncertain or incorrect results with full confidence. Gold layer data carries the guarantee that quality has already been enforced structurally.

## Related

- [[Data Quality]] — the quality practices the Medallion Architecture enables
- [[Delta Lake]] — the table format all three layers are built on
- [[LakeFlow]] — the pipeline orchestration tool that moves data between Bronze, Silver, and Gold
- [[Genie Agents]] — should always connect to Gold layer tables
- [[Unity Catalog]] — governance and metadata layer that spans all three layers
- [[Databricks]] — platform where the architecture is implemented with Delta Lake
