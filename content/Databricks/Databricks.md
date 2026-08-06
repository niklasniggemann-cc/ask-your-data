---
title: Databricks
type:
  - "[[Technology]]"
  - "[[Product]]"
category: Data Intelligence Platform
tags:
  - databricks
---

## Definition

Databricks is a data intelligence platform combining data engineering, analytics, machine learning, and AI in a unified lakehouse architecture. Built on Apache Spark and [[Delta Lake]], with [[Unity Catalog]] as its governance layer.

## Core Platform Components

- **[[Delta Lake]]** — open table format providing ACID transactions and versioning on data lakes
- **[[Unity Catalog]]** — unified governance: metadata, access control, lineage, and data discovery
- **Databricks SQL** — serverless SQL analytics with Pro and Serverless warehouse options
- **[[LakeFlow]]** — data pipeline orchestration (formerly Workflows + Delta Live Tables)
- **Model Serving** — deploy and scale ML and AI models

## Natural Language AI Products

Databricks bundles its natural language data access capabilities under the AI/BI umbrella:

- **[[Genie Agents]]** — curated natural-language chat over approved tables
- **[[Genie One]]** — unified full-screen AI chat across all agents and content
- **[[Genie Code]]** — AI coding assistant for developers inside the workspace

## Governance Architecture

[[Unity Catalog]] is the single governance layer across all workloads. [[Agent Metadata]] attaches structured business context to [[Metric Views]] inside Unity Catalog. The [[Medallion Architecture]] organizes data into Bronze → Silver → Gold layers within the platform.

## Related

- [[Unity Catalog]] — governance foundation
- [[Delta Lake]] — storage layer
- [[LakeFlow]] — data pipeline orchestration
- [[Lakebase]] — serverless Postgres for agent memory and operational workloads
- [[Agent Bricks]] — governed agent platform
- [[Genie Agents]] — AI data interface
- [[Medallion Architecture]] — data quality layering pattern
- [[Semantic Layer]] — business meaning layer that Databricks exposes via Unity Catalog
- [[Agent Skills]] — Databricks-maintained skill packages for AI coding assistants
