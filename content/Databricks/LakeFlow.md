---
title: LakeFlow
aliases:
  - Lakeflow
  - Delta Live Tables
  - Databricks Workflows
type: "[[Technology]]"
vendor: "[[Databricks]]"
category: Data Pipeline Orchestration
tags:
  - databricks
---

## Definition

LakeFlow is Databricks' unified data engineering solution consolidating ingestion, transformation, and orchestration into one product. Announced at DAIS 2025, it unified two formerly separate products — **Delta Live Tables** (now Lakeflow Declarative Pipelines) and **Databricks Workflows** (now Lakeflow Jobs) — and added **Lakeflow Connect** for managed ingestion from external systems.

## Three Components

### Lakeflow Connect

Managed data ingestion connectors — high-throughput, low-latency pipelines from external systems into [[Delta Lake]]. Connectors as of Aug 2026:
- **GA**: SharePoint, Google Drive
- **Beta**: PagerDuty (incidents, on-call, services), Veeva Vault, MySQL CDC, OpenAI (org admin data: users, projects, API keys, usage, costs, audit logs), Anthropic (compliance audit logs, directory data, Claude chat/message data)
- Row filtering GA for Google Analytics, Salesforce, ServiceNow, and query-based connectors
- All Lakeflow Connect pipelines auto-record source lineage in [[Unity Catalog]]

The OpenAI and Anthropic connectors let organizations pull their own AI-vendor usage, cost, and compliance data into the governed lakehouse — the same FinOps/governance pattern LakeFlow already applies to SaaS tools, now extended to AI spend itself.

### Lakeflow Declarative Pipelines (formerly Delta Live Tables)

SQL-based declarative ETL. Define transformations; LakeFlow infers the dependency graph, determines execution order, handles retries, and manages data quality checks. Primary implementation vehicle for the [[Medallion Architecture]] (Bronze → Silver → Gold refinement). Serverless compute integrated.

### Lakeflow Jobs (formerly Databricks Workflows)

Workflow orchestration for production pipelines. Schedules and monitors declarative pipelines, notebooks, arbitrary tasks, and external integrations (Apache Airflow, Azure Data Factory). As of August 2026: schedule directly from the pipeline page.

## Role in the Data Stack

LakeFlow is the ingestion and transformation layer upstream of everything else. The output of LakeFlow pipelines becomes the Gold-layer input that [[Genie Agents]], dashboards, and AI workloads consume.

```
External systems → Lakeflow Connect → Bronze (Delta)
                                    → Lakeflow Declarative → Silver → Gold
                                                                     → Genie Agents / BI
```

## Related

- [[Delta Lake]] — the table format LakeFlow writes to
- [[Medallion Architecture]] — the layered pattern LakeFlow Declarative implements
- [[Unity Catalog]] — governance layer; all pipelines governed here, lineage auto-recorded
- [[Data Lineage]] — LakeFlow Connect auto-records source-to-sink lineage
- [[Data Quality]] — LakeFlow Declarative enforces quality constraints at ingestion and transformation
- [[Databricks]] — parent platform
