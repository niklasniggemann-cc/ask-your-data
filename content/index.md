---
title: Home
tags:
  - home
---

# Ask Your Data — Research Vault

A knowledge base on building trustworthy natural-language data interfaces — covering Databricks Genie Agents, the infrastructure beneath them, and the engineering practices required to keep GenAI systems reliable in production.

---

## How to Navigate

**Graph view** (`Cmd+Shift+G`) is the best starting point. Each colour represents a cluster:

| Colour | Cluster | What's in it |
|--------|---------|-------------|
| 🟠 Orange-red | Genie | The Databricks AI product family |
| 🟡 Amber | Databricks | Platform, Unity Catalog, data quality |
| 🔵 Blue | Semantic | Semantic layer, NL-to-SQL, disambiguation |
| 🟣 Purple | AI Quality | Evaluation, the Data Flywheel, observability |
| 🟢 Green | Frameworks | MLflow, LangGraph, DSPy, MCP |

In the graph: **click any node** to highlight its direct connections. **Right-click → Open** to jump to the note.

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
- [[Knowledge Store]] — the space-level semantic store that extends Unity Catalog

### The Data Platform
- [[Databricks]] — the platform everything runs on
- [[Unity Catalog]] — unified governance: metadata, access control, lineage
- [[Agent Metadata]] — YAML-defined business context (display names, synonyms, formats)
- [[Medallion Architecture]] — Bronze → Silver → Gold data quality layering
- [[Data Quality]] — six dimensions, Databricks tools, Genie-specific practices

### Shared Business Meaning
- [[Semantic Layer]] — the architectural layer that makes NL interfaces trustworthy
- [[Natural Language to SQL]] — how it works and where it fails without governance
- [[Disambiguation]] — structural vs. dynamic approaches to resolving ambiguous queries

### GenAI Engineering
- [[GenAI Technical Debt]] — the four debt categories unique to GenAI systems
- [[Data Flywheel]] — the three-step feedback loop for continuous quality improvement
- [[Evaluation]] — why it's the highest-leverage activity in GenAI
- [[LLM-as-a-Judge]] — evaluating subjective outputs at scale
- [[Observability]] — making pipeline internals visible enough to debug

---

## What This Vault Is Not

These notes capture *how things work and why they're designed that way* — not step-by-step tutorials or official documentation. For official docs, see the Databricks documentation links in [[Genie Agents]].
