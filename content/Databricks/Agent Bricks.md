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
