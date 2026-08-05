---
title: Home
tags:
  - home
---

# Ask Your Data — Research Vault

A knowledge base on building trustworthy natural-language data interfaces — covering [[Databricks]] [[Genie Agents]], the infrastructure beneath them, and the engineering practices required to keep GenAI systems reliable in production.

---

## How to Navigate

- **Graph** (right sidebar) — shows connections between the current note and its neighbours. Click any node to jump to that note.
- **Backlinks** (right sidebar, below the graph) — lists every note that links to the current one.
- **Explorer** (left sidebar) — browses notes by folder: Genie, Databricks, Semantic, AI Quality, Frameworks.
- **Search** (top left) — full-text search across all notes.

---

## The Core Idea

Natural-language data interfaces look simple from the outside — ask a question, get an answer. Making them *trustworthy* requires a layered foundation:

**Clean data** ([[Medallion Architecture]]) → **governed metadata** ([[Unity Catalog]], [[Agent Metadata]]) → **shared business meaning** ([[Semantic Layer]], [[Knowledge Store]]) → **AI interface** ([[Genie Agents]], [[Genie One]]) → **continuous improvement** ([[Data Flywheel]])

Skipping any layer creates debt that surfaces as confident-sounding wrong answers.

---

## Entry Points by Topic

### The Genie Product Family
- [[Genie Agents]] — curated NL chat over approved tables; setup, API, best practices, permissions
- [[Genie One]] — unified chat across all agents and external sources
- [[Genie Code]] — AI coding assistant for developers inside the workspace
- [[Genie Ontology]] — continuously-learned org-wide context layer (OntoRank)
- [[Knowledge Store]] — the space-level semantic store that extends [[Unity Catalog]]

### The Data Platform
- [[Databricks]] — the platform everything runs on
- [[Unity Catalog]] — unified governance: metadata, access control, lineage
- [[Agent Metadata]] — YAML-defined business context (display names, synonyms, formats)
- [[Agent Bricks]] — governed agent platform (Supervisor, Document Intelligence, managed memory)
- [[Lakebase]] — serverless Postgres for agent memory and operational workloads
- [[LakeFlow]] — data pipeline orchestration (ingestion, transformation, jobs)
- [[Medallion Architecture]] — Bronze → Silver → Gold data quality layering
- [[Data Quality]] — six dimensions, Databricks tools, Genie-specific practices
- [[Lakehouse Monitoring]] — metric tables and dashboards for tracking data quality over time

### Shared Business Meaning
- [[Semantic Layer]] — the architectural layer that makes NL interfaces trustworthy
- [[Natural Language to SQL]] — how it works and where it fails without governance
- [[Disambiguation]] — structural vs. dynamic approaches to resolving ambiguous queries
- [[Hallucinations]] — the failure mode when AI gets it confidently wrong

### GenAI Engineering
- [[GenAI Technical Debt]] — the four debt categories unique to GenAI systems
- [[Data Flywheel]] — the three-step feedback loop for continuous quality improvement
- [[Evaluation]] — why it's the highest-leverage activity in GenAI
- [[LLM-as-a-Judge]] — evaluating subjective outputs at scale
- [[Observability]] — making pipeline internals visible enough to debug
- [[RAG]] — retrieval-augmented generation for unstructured document queries

### Frameworks & Tools
- [[MLflow]] — experiment tracking and GenAI evaluation
- [[LangGraph]] — graph-based stateful agent orchestration
- [[DSPy]] — declarative LLM programming and prompt optimization
- [[MCP]] — Model Context Protocol for AI tool connectivity
- [[MotherDuck]] — serverless DuckDB analytics with MCP server
- [[Omnigent]] — meta-harness for composing and governing agents across frameworks
- [[Updates]] — running log of confirmed Databricks developments from the daily briefing

---

## What This Vault Is Not

These notes capture *how things work and why they're designed that way* — not step-by-step tutorials or official documentation. For official docs, see the Databricks documentation links in [[Genie Agents]].
