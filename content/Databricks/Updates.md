---
title: Updates
tags:
  - databricks
  - changelog
---

# Databricks GenAI — Update Log

Running log of confirmed developments surfaced by the daily briefing skill. Newest entries first.

## 2026-08-05 (second run)

_Delta-only — checked against the same-day entry below. Official Databricks sources (platform release notes, AI/BI release notes) showed no new dated items since the first run today._

**Ecosystem / Open Source**
- **OntoBricks** (databrickslabs, actively maintained — 199 stars, 458+ commits) — transforms Unity Catalog tables into a materialized, reasoned knowledge graph (OWL ontology design, R2RML mapping, Delta-backed triple store + Lakebase Postgres graph engine, OWL 2 RL/SWRL/SHACL reasoning), queryable via auto-generated GraphQL and an MCP server. Community project, not an official Databricks product. New note created: [[OntoBricks]]. [Source](https://github.com/databrickslabs/ontobricks)

## 2026-08-05

**Partnerships**
- **Microsoft and Databricks extended their strategic partnership into the 2030s** (announced July 23). Databricks is moving its own internal business operations onto Azure Databricks and adopting Azure Cobalt 200 (Arm-based infra, ~50% perf improvement). Genie, Genie Ontology, and Unity AI Gateway are being integrated directly into Microsoft 365, Teams, Copilot, Power BI, and Purview. [Source](https://news.microsoft.com/source/2026/07/23/databricks-and-microsoft-expand-partnership-to-help-enterprises-bring-business-context-to-enterprise-ai/)

**Mosaic AI / Agent Framework**
- **Omnigent open-sourced** (Apache 2.0, June) — a new "meta-harness" category that sits above agent frameworks (Claude Code, Codex, Pi), letting teams compose, govern, and share agents from one layer. Enforces guardrails (cost budgets, permissions) statefully at the harness level rather than via prompts an agent could reason around; sandboxes filesystem/network access; supports live shared agent sessions. Databricks offers a fully managed version. Might be worth a new concept note — no existing note covers this. [Source](https://www.databricks.com/blog/introducing-omnigent-meta-harness-combine-control-and-share-your-agents)
- **Agent Bricks expanded framework support** — now builds on Claude Code SDK, LangGraph, Agno, CrewAI, and OpenAI Agent SDK, with horizontal autoscaling via Databricks Apps. Databricks cites 100K+ agents built and 1+ quadrillion tokens/year processed on the platform. [Source](https://www.databricks.com/blog/agent-bricks-dais-2026)

**Ask Your Data / Genie / AI-BI**
- **Genie One**: chats can now be shared read-only account-wide; added connections to Gmail plus Teams/Outlook/Calendar in Microsoft 365; a Genie Agent can now read files sitting in Unity Catalog volumes (PDFs, slide decks, images) rather than only structured tables. Updates [[Genie One]].
- **Chart explain-in-place** — right-click a bar/line/area time-series visualization and ask Genie to explain a change; it enters Agent Mode to identify top drivers automatically. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

**Model Serving / Foundation Model APIs**
- **Gemini 2.5 Pro** (Google's hybrid reasoning model, "Deep Think" mode, built-in audio output) now available via Databricks Foundation Model APIs on pay-per-token pricing, alongside existing hosted models like Llama 3.3 70B. [Source](https://docs.databricks.com/aws/en/machine-learning/foundation-model-apis/supported-models)

**MLflow / GenAI Observability**
- **MLflow 3 tracing** now runs on a production-scale trace-ingestion backend for real-time observability. Databricks now recommends storing traces in Unity Catalog for new/production workloads — queryable via SQL like any Delta table, governed the same way. Automatic instrumentation spans 20+ frameworks. Updates [[MLflow]]. [Source](https://docs.databricks.com/aws/en/mlflow3/genai/tracing/)

**Vector Search / AI Search** (backfilled from DAIS 2026 — missed in the first run)
- **Lakebase Search announced** (June 16) — hybrid vector + full-text retrieval built directly into Lakebase Postgres via two new extensions, `lakebase_vector` (pgvector-compatible ANN search, ~32x index compression via RaBitQ, scales past 1B vectors) and `lakebase_text` (BM25 full-text without GIN's RAM bloat). Beta on AWS and Azure. Distinct from the already-noted Vector Search → AI Search rebrand: AI Search is the fully managed option, Lakebase Search is the Postgres-native one for agent memory/retrieval on a single backend. New note created: [[Lakebase Search]]. Also created [[AI Search]] to formally cover the rebrand flagged in the 2026-08-04 entry below. [Source](https://www.databricks.com/blog/announcing-lakebase-search-agent-native-retrieval-built-lakebase-postgres)

**Unity Catalog / Governance**
- **Unity AI Gateway is now formally GA** (August 4 release notes) — was announced/previewed at DAIS 2026 (see below); service policies and agent services remain in Beta. Updates [[Unity Catalog]]. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

**Ask Your Data / Genie / AI-BI**
- **Full page Genie Code is now GA** (August 4) — command-center layout: active chat prominent, notebooks/files open as tabs alongside it, multiple parallel chats, personalization via skills/instructions/MCP servers. Updates [[Genie Code]]. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

**LakeFlow**
- **SharePoint connector now GA** and **Google Drive connector now GA** in Lakeflow Connect (August 4). **PagerDuty connector** now in Beta — ingests incident, on-call, service, and audit data. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

## 2026-08-04

_First run for this project — no prior baseline, so this entry is broader than a typical daily delta._

**Ask Your Data / Genie / AI-BI**
- **Genie One + Genie Agents free usage extended to January 31, 2027** (previously ended July 31, 2026). Service principal usage is still billed; budget controls don't apply during the promo. Updates the pricing note in [[Genie Agents]]. [Source](https://learn.microsoft.com/en-us/azure/databricks/genie/monitor-cost)
- **Genie Ontology** — a continuously learned enterprise context layer, built on Unity Catalog Glossary/Domains, now feeds Genie so it understands business concepts without per-agent configuration. Announced at DAIS 2026. [Source](https://www.databricks.com/blog/introducing-genie-one-genie-ontology-and-genie-agents)
- **Genie One: Ontology snippets** now in Public Preview. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)
- AI/BI dashboards can now **import Power BI and Tableau reports directly** as a new dashboard from the dashboard list page. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

**Mosaic AI / Agent Framework**
- **Agent Bricks Supervisor Agent is now GA** — orchestrates multiple enterprise agents. [Source](https://www.databricks.com/blog/agent-bricks-supervisor-agent-now-ga-orchestrate-enterprise-agents)
- **Agent Bricks Document Intelligence is now GA** — SQL functions `ai_parse_document`, `ai_extract`, `ai_classify` for document parsing/analysis at scale. [Source](https://www.databricks.com/blog/agent-bricks-dais-2026)
- **Managed memory for agents**, powered by Lakebase — agents can persist context and session history across sessions without custom infrastructure. [Source](https://www.databricks.com/blog/agent-bricks-dais-2026)

**Unity Catalog / Governance** (see also [[Unity Catalog]])
- **Unity AI Gateway** — new runtime governance layer for models, agents, tools, and MCP connections. **Contextual Service Policies** (now Beta) let admins allow/deny/require-approval for specific agent actions (e.g. writing to sensitive folders). AI Gateway budgets now also cover external, bring-your-own-key providers. [Source](https://www.databricks.com/blog/whats-new-unity-catalog-data-ai-summit-2026)
- **ABAC Grant Policies** in Beta for models — define attribute-based access once, auto-grant EXECUTE across matching models. Identity Attributes and Context Attributes coming soon in preview.
- **Glossary** (coming soon) and **Domains** (Public Preview) — shared, governed business terminology and business-aligned data organization, both feeding Genie Ontology.
- **External Lineage now GA** — extends Unity Catalog lineage to non-Databricks source/downstream systems; Lakeflow Connect pipelines auto-record source lineage. Updates [[Data Lineage]]. [Source](https://docs.databricks.com/aws/en/data-governance/unity-catalog/external-lineage)
- **Cross-cloud, cross-region addressability** — new four-level namespace (`metastore.catalog.schema.table`) gives every asset one address across a whole Databricks footprint.
- **Metrics** (formerly Metric Views) significantly expanded: multi-fact relationships (Public Preview in Dashboards), level-of-detail calculations, parameterized metrics, query Materialization (Public Preview), and import from Power BI/Tableau (Beta). Updates [[Metric Views]].

**Vector Search / AI Search**
- **Databricks Vector Search has been rebranded to "AI Search"** (Python SDK now `databricks-ai-search`). Might be worth a new concept note — no existing note covers this product.
- **Storage Optimized AI Search endpoints** — new deployment option for billion-scale vector indexes, decoupling storage (cloud object storage) from compute. Builds billion-vector indexes in under 8 hours (20x faster than Standard), up to 7x lower serving cost, using a custom IVF + Product Quantization architecture with a Rust query engine. Trade-off: ~300–500ms query latency vs. 20–50ms on Standard endpoints. [Source](https://www.databricks.com/blog/decoupled-design-billion-scale-vector-search)
- **`ai_prep_search`** SQL function in Beta — transforms `ai_parse_document` output into search-ready chunks for RAG pipelines.
- Built-in **retrieval quality evaluation** for comparing search strategy relevance.

**LakeFlow**
- **Row filtering in Lakeflow Connect is now GA** — ingest only rows matching a condition, applied on both initial load and incremental updates; supported for Google Analytics, Salesforce, ServiceNow, and all query-based connectors.
- **Veeva Vault connector** in Beta (via Veeva's Direct Data API).
- **Integrated MySQL CDC pipeline** in Beta — combines extraction and application into a single pipeline.
- Simplified continuous pipeline/job configuration (schedule directly from the pipeline page) — announced for early August 2026, not yet confirmed live as of this run.

_Note: this first run surfaced an unusually large backlog since there's no prior baseline — expect future entries to be much shorter, delta-only updates._
