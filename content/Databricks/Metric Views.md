---
title: Metric Views
type: "[[Technology]]"
vendor: "[[Databricks]]"
governed-in: "[[Unity Catalog]]"
category: Semantic Object
tags:
  - databricks
---

## Definition

Metric Views are governed semantic objects in [[Unity Catalog]] that define a layer of business meaning over source tables. They specify measures, dimensions, and relationships in a structured format — and are the construct that [[Agent Metadata]] is attached to.

They are the primary vehicle for making data semantically queryable by AI tools like [[Genie Agents]] without requiring those tools to reason directly against raw schemas.

## Structure

A Metric View defines:

- **Source** — the underlying Unity Catalog table or view
- **Measures** — aggregated numeric values (e.g., `SUM(rev_mrr_usd)`) with display names, synonyms, and format specs
- **Dimensions** — grouping attributes (e.g., `region_code`) with display names and synonyms

All expressed in YAML (version 1.1, requires Databricks Runtime 17.3).

## Recent Expansion (Aug 2026)

Metric Views (rebranded "Metrics" in some surfaces) gained several capabilities:

- **Multi-fact relationships** (Public Preview, in Dashboards) — a single metric definition can span measures from more than one fact table, instead of requiring one fact table per view.
- **Level-of-detail calculations** — aggregate at a grain different from the query's grouping, without a separate pre-aggregated table.
- **Parameterized metrics** — metric definitions accept parameters (e.g., a lookback window) rather than requiring a fixed variant per use case.
- **Query materialization** (Public Preview) — materializes metric query results for performance, rather than recomputing against source tables on every request.
- **Import from Power BI/Tableau** (Beta) — existing BI-tool metric definitions can be imported directly into Metric Views instead of being redefined by hand.

## Role in the AI Stack

When [[Agent Metadata]] is attached to a Metric View, the combination gives AI tools:
1. Governed, auditable metric definitions (not raw column inference)
2. Business vocabulary (synonyms resolve "churn" to the correct measure deterministically)
3. Consistent formatting (3.4% not 0.034)

This is the structural answer to the limitation of pure [[Natural Language to SQL]] — queries are made against sanctioned definitions, not raw tables.

## Related

- [[Agent Metadata]] — the YAML business context attached to Metric Views
- [[Unity Catalog]] — where Metric Views are governed
- [[Semantic Layer]] — the architectural concept Metric Views implement in Databricks
- [[Genie Agents]] — primary AI consumer
- [[Natural Language to SQL]] — the less governed alternative
