---
title: Data Lineage
type: "[[Concept]]"
context: Data Engineering, Data Governance
tags:
  - semantic
  - databricks
---

## Definition

Data lineage is the tracking of data's origin, movement, and transformation throughout its lifecycle — from source systems through transformation pipelines to consuming applications. It answers: where did this data come from, what changed it, and what depends on it?

## Why It Matters

Lineage serves three core functions:

1. **Impact analysis** — before modifying a table or column, lineage shows which downstream dashboards, models, and AI tools will be affected
2. **Audit trails** — traceable provenance for regulatory compliance and debugging
3. **Trust** — users and AI tools can understand the path data took before they see it

In the context of the [[Semantic Layer]], lineage tracks which source tables feed each metric definition and which consuming systems depend on it.

## In Databricks

[[Unity Catalog]] tracks lineage automatically across all workloads in the platform — SQL queries, notebooks, Lakeflow pipelines, and ML models. Column-level lineage shows exactly which source columns contribute to each output column, without requiring manual annotation.

## Related

- [[Unity Catalog]] — primary lineage tracking system in Databricks
- [[Data Governance]] — lineage as a structural governance component
- [[Semantic Layer]] — where lineage connects source data to metric definitions
- [[Medallion Architecture]] — the layers lineage flows through (Bronze → Silver → Gold)
