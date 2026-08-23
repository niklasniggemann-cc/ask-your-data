---
title: Agent Bricks
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Enterprise Agent Platform
tags:
  - databricks
---

## Definition

Agent Bricks is Databricks' governed enterprise agent platform for building, deploying, and governing AI agents that operate on business data. It unifies model access, execution, governance, and context — reporting 100K+ agents built and 1+ quadrillion tokens/year processed. Builds on multiple frameworks (Claude Code SDK, LangGraph, Agno, CrewAI, OpenAI Agent SDK) with horizontal autoscaling via Databricks Apps.

## Core Components

### Supervisor Agent (GA)

Orchestrates multiple enterprise agents from a single entry point. Uses **On-Behalf-Of (OBO) authentication** — the supervisor acts as a transparent proxy for the human user, so each sub-agent sees the correct user identity and [[Unity Catalog]] permissions apply automatically. Manages task delegation, inter-agent coordination, and result synthesis.

### Document Intelligence (GA)

SQL functions for intelligent document processing at scale:

| Function | Purpose |
|----------|---------|
| `ai_parse_document` | Multimodal document parsing — tables, figures, diagrams |
| `ai_extract` | Structured data extraction from unstructured documents |
| `ai_classify` | Document classification |
| `ai_prep_search` (Beta) | Transforms parsed documents into search-ready chunks for [[RAG]] pipelines |

Covers ~80% of enterprise unstructured data volume. More cost-efficient than third-party document APIs.

**Precision Mode** (`ai_extract`, added Aug 2026) — an optional extraction mode pairing custom fine-tuned extraction models with an agentic harness that decomposes large documents, runs sub-agent extraction in parallel, and reconciles results into a single structured output. Purpose-built for three cases where single-call or chunk-and-merge extraction breaks down: long documents (up to 2,000 pages) needing cross-page reconciliation, large nested outputs (thousands of line items), and reasoning-heavy schemas (300+ nested fields). Benchmarked at 94.7% accuracy across ~9,000 complex documents, 7 points ahead of the strongest frontier-model baseline. Enabled via `mode: precision` in `ai_extract` or a toggle in the Information Extraction UI.

## Recent Developments

- **2026-08-19** — Precision Mode for `ai_extract` (launched Aug 18, see above) reached **General Availability** the following day. [Source](https://learn.microsoft.com/en-us/azure/databricks/sql/language-manual/functions/ai_extract)
- **2026-08-18** — Precision Mode launched for `ai_extract`, see above. [Source](https://www.databricks.com/blog/databricks-document-intelligence-pushing-frontier-complex-document-extraction)

### Managed Memory

Agents persist context and session history across sessions via [[Lakebase]] — a governed Postgres backend — without custom infrastructure. Replaces in-context or ephemeral state management with queryable, auditable storage.

## Framework Support

Agent Bricks supports building agents on top of:
- Claude Code SDK
- [[LangGraph]]
- Agno
- CrewAI
- OpenAI Agent SDK

Agents deploy with horizontal autoscaling via Databricks Apps.

## Governance Model

Every Agent Bricks component is governed through [[Unity Catalog]]:
- OBO authentication enforces per-user data access at every agent call
- Tool costs and permissions managed in Unity AI Gateway
- Agent actions auditable via Unity Catalog lineage

## Related

- [[Unity Catalog]] — governance layer: OBO auth, tool permissions, audit
- [[Lakebase]] — managed memory backend for persistent agent state
- [[Genie Agents]] — specialized agents that Agent Bricks Supervisor orchestrates
- [[LangGraph]] — supported orchestration framework
- [[MLflow]] — observability and tracing for Agent Bricks deployments
- [[RAG]] — Document Intelligence feeds RAG pipelines via `ai_prep_search`
- [[Omnigent]] — meta-harness that can sit above Agent Bricks for cross-framework governance
- [[Databricks]] — parent platform
- [[MCP]] — integrated for tool connectivity across Agent Bricks agents
