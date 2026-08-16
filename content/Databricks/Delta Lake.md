---
title: Delta Lake
type: "[[Technology]]"
vendor: "[[Databricks]]"
category: Open Table Format
license: Open Source (Apache 2.0)
tags:
  - databricks
---

## Definition

Delta Lake is an open-source storage layer that brings ACID transactions, scalable metadata handling, and data versioning to data lakes. It is the storage foundation of the Databricks lakehouse and the format used across all layers of the [[Medallion Architecture]].

## Key Properties

- **ACID transactions** — atomicity, consistency, isolation, durability guarantees on data lake storage
- **Time travel** — query data as it existed at any prior point using `VERSION AS OF` or `TIMESTAMP AS OF`
- **Schema enforcement and evolution** — reject writes that violate schema, or safely evolve it
- **Scalable metadata** — handles tables with billions of rows and thousands of partitions efficiently
- **Unified batch and streaming** — same table serves both batch and streaming workloads

## Role in Data Quality

Delta Lake's ACID guarantees mean that [[Data Quality]] practices like deduplication via MERGE operations, schema enforcement during ingestion, and constraint-based blocking of invalid records are reliable by construction. This is the platform foundation that makes the [[Medallion Architecture]]'s Bronze → Silver → Gold refinement trustworthy.

## Related

- [[Databricks]] — primary maintainer and platform
- [[Medallion Architecture]] — the layering pattern built on Delta Lake tables
- [[LakeFlow]] — orchestrates pipelines that read and write Delta tables
- [[Unity Catalog]] — governs Delta tables with access control, lineage, and metadata
- [[Data Quality]] — quality practices that Delta Lake's guarantees enable
- [[Lakebase]] — analytical complement; Delta Lake handles OLAP, Lakebase handles OLTP
