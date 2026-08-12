---
title: Data Quality
type: "[[Concept]]"
context: Data Engineering, AI Analytics
tags:
  - databricks
  - ai-quality
---

## Definition

Data quality determines whether AI tools deliver value or confusion. LLMs don't amplify poor data quality — they wrap it in confident-sounding prose. The principle: **Garbage In, Confident Garbage Out**.

## The Six Dimensions

| Dimension | Definition |
|-----------|------------|
| **Consistency** | Data values don't conflict across systems |
| **Completeness** | No missing information |
| **Accuracy** | Error-free data |
| **Validity** | Conformance to required formats |
| **Uniqueness** | No duplicates |
| **Timeliness** | Up-to-date information |

Accuracy is the most critical dimension for AI tools — AI confidence can mislead, especially non-technical users.

## Platform-Level Quality (Databricks)

- **[[Lakehouse Monitoring]]** — tracks all six dimensions; creates metric tables and auto-generated dashboards that visualize quality metrics over time
- **Ingestion controls** — block invalid data via constraints, quarantine problematic records, or flag violations; schema enforcement via Auto Loader
- **[[Medallion Architecture]]** — structured refinement through Bronze → Silver → Gold layers

[[Genie Agents]] should connect to Gold layer tables whenever possible — data is already cleaned and validated.

## Metadata and Business Context

Databricks allows adding metadata at multiple levels: databases, tables, columns, individual commits. Well-annotated datasets are searchable, auditable, and far easier for AI to interpret.

Every Genie Agent is built on [[Unity Catalog]]-registered data — Genie uses the metadata attached to those objects.

See [[Knowledge Store]] for the space-level semantic store that extends UC metadata.

## Prompt Matching

Two components that help Genie interpret natural language:

- **Format assistance** — provides representative values for eligible columns; helps Genie understand data types and formatting patterns
- **Entity matching** — curates lists of distinct values (up to 120 columns, 1,024 values per column) for fields users commonly reference (states, product categories, customer segments)

Together they allow Genie to match conversational phrasing to actual column names, correct spelling errors, and map user terminology to database values.

## Encoding Business Logic

Mechanisms for grounding Genie in correct business logic:

| Mechanism | Purpose |
|-----------|---------|
| Example SQL queries | Static or parameterised; teach Genie how to handle common prompt formats |
| SQL functions in [[Unity Catalog]] | Complex logic as reusable functions; responses marked **Trusted** |
| Join relationships | Define how tables connect so Genie doesn't guess |
| SQL expressions | Structured definitions for KPIs, business attributes, and conditions |

Parameterised example queries produce responses marked **Trusted** — signals to users that results follow established logic.

## Benchmarking

Test question sets (up to 500 per space) that assess Genie response accuracy:
- Each question optionally includes a ground-truth SQL query or Unity Catalog SQL function
- Genie compares generated results against ground truth
- Automated tagging makes it easy to identify problems at a glance
- Run regularly as the space is refined

Best benchmark practices:
- Cover questions users ask most often
- Include multiple phrasings of the same question
- Use realistic formats that mirror how users actually talk

See [[Genie Agents]] for full benchmark configuration details.

## Related

- [[Medallion Architecture]] — the three-layer data refinement pattern
- [[Knowledge Store]] — space-level semantic definitions for Genie
- [[Genie Agents]] — the primary AI consumer of data quality practices
- [[Unity Catalog]] — metadata and governance layer
- [[Semantic Layer]] — the broader architecture that governs business meaning
- [[Lakehouse Monitoring]] — tracks the six data quality dimensions over time via metric tables and dashboards
