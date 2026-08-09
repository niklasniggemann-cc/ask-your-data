---
title: Updates
tags:
  - market-landscape
  - changelog
---

# Ask Your Data — Market Landscape Update Log

Running log of confirmed developments across the broader natural-language-to-data market — every vendor and open-source project outside Databricks (which has its own log, see [[Databricks/Updates|Databricks Updates]]). Newest entries first.

## 2026-08-09

**ThoughtSpot**
- **Named a Leader in the 2026 Gartner Magic Quadrant for Analytics and BI Platforms** (Jul 1) — Gartner specifically cited ThoughtSpot's conversational analytics, external semantic-layer connectivity, and agent workflow orchestration as strengths. [Source](https://www.globenewswire.com/news-release/2026/07/01/3320829/0/en/thoughtspot-named-a-leader-in-the-2026-gartner-magic-quadrant-for-analytics-and-bi-platforms.html)

**Snowflake**
- **Snowflake Intelligence renamed Snowflake CoWork; Cortex Code renamed Snowflake CoCo** (Snowflake Summit, Jun) — a positioning shift, not just a name change: CoWork is pitched as a "colleague" that participates in workflows rather than a BI assistant. Bundled with a push toward GA for Skills (natural-language workflow automation), MCP connectors (Google Workspace, Jira, Salesforce, Slack), Deep Research, a mobile app, and reusable artifacts. Note for future searches: use "Snowflake CoWork," not "Snowflake Intelligence," going forward. [Source](https://www.constellationr.com/insights/news/snowflake-rolls-out-snowflake-intelligence-cortex-code-updates)

**Hex**
- **Hex Agent now accessible via CLI and API** (Jul 30) — previously notebook/browser-only; agent conversations can now run from external tools and scripts. Also ships visibility into which resources the agent used per step, an upgrade to Claude Opus 5, and up to 10x faster Snowflake schema refreshes (incremental fetch instead of full warehouse rescans). [Source](https://learn.hex.tech/changelog/2026-07-30)

**Microsoft**
- **Fabric Skills for GitHub Copilot, Claude, and CLI** (Build 2026, Jun) — open-source toolkit, distinct from the previously-logged Copilot in web modeling, that lets AI coding agents directly author/query Power BI semantic models and other Fabric assets (SQL warehouse, Lakehouse, Eventhouse, Dataflows Gen2). Microsoft built it and opened it to community contribution. [Source](https://community.fabric.microsoft.com/t5/Fabric-Updates-Blog/Fabric-Skills-for-GitHub-Copilot-Claude-and-CLI-built-by/ba-p/5190188)

**Amazon**
- **Amazon Q Business closes to new customers** (Jul 31) — existing customers keep support and bug fixes but no new features; AWS is directing new generative-BI and agentic-AI workloads to Amazon Quick (the QuickSight-descended suite) instead. [Source](https://docs.aws.amazon.com/amazonq/latest/qbusiness-ug/qbusiness-availability-change.html)

_Note: Google Cloud Conversational Analytics GA (Jul 29), Gartner's >50% natural-language-query stat, and Sigma's Ask Sigma/MCP-for-ChatGPT rollout were all resurfaced by this run's search but are already logged in the 2026-08-08 entry below with no meaningful delta — not re-added. ThoughtSpot Spotter Semantics (Mar 16) and Spotter for Industries (Mar 19, already logged) also resurfaced but are old ground._

## 2026-08-08

_First run — this task's vault connection had lapsed, so this entry backfills confirmed developments from roughly the last seven months rather than just the last 24 hours. Future runs will dedup against this log and report genuinely daily deltas._

**Google Cloud / Looker**
- **Conversational Analytics now spans the full Google data estate** (GA + new previews, Jul 29) — BigQuery Conversational Analytics and the Conversational Analytics API reached GA, joining Looker's Conversational Analytics (GA a year earlier). New in preview: Conversational Analytics in Databases (AlloyDB, Cloud SQL, Spanner), and "Agentic Workflows" — scheduled agents that proactively run multi-factor anomaly deep-dives and push summaries to chat instead of waiting to be asked. [Source](https://cloud.google.com/blog/products/data-analytics/conversational-analytics-in-google-data-cloud-in-q326)

**Sigma Computing**
- **Ask Sigma upgraded to Sigma Assistant** (Apr 17) — new MCP server, enhanced semantic search, AI-context-aware data models.
- **One-click Sigma MCP install for ChatGPT** (Jul 31) — ChatGPT can now query Sigma data directly via a Sigma plugin, without a custom integration. [Source](https://help.sigmacomputing.com/changelog/2026-04-17)

**Semantic layers / Text-to-SQL**
- **dbt's 2026 semantic-layer-vs-text-to-SQL benchmark** (Apr 7) — rerun with current-gen models (Sonnet 4.6, GPT-5.3 Codex). Text-to-SQL accuracy nearly doubled since 2023 (32.7% → 64.5%), but the dbt Semantic Layer still hits ~98–100% on covered queries because its query generation is deterministic — it errors out rather than silently guessing wrong on questions outside what's modeled. dbt's recommendation: semantic layer for anything accuracy-critical, text-to-SQL for ad hoc exploration. Updates [[Semantic Layer]]. [Source](https://docs.getdbt.com/blog/semantic-layer-vs-text-to-sql-2026)
- **Open Semantic Interchange (OSI) v1.0 spec released** (Jan 27) — Apache 2.0, YAML-based cross-vendor semantic-layer standard (metrics, dimensions, relationships) backed by Snowflake, dbt Labs, Cube, AtScale, Salesforce, Tableau, and 40+ others, aimed at one portable metric definition instead of redefining business logic per BI tool. Updates [[Semantic Layer]]. [Source](https://open-semantic-interchange.org/updates/)

**Snowflake**
- **Cortex Code + Semantic View Autopilot reach GA** (Feb 3) — Cortex Code is a data-native coding agent; Semantic View Autopilot auto-maintains business-metric definitions and can keep semantic logic in sync across dbt, Looker, Sigma, and ThoughtSpot via OSI connections. [Source](https://www.constellationr.com/insights/news/snowflake-cortex-code-semantic-view-autopilot-ga)

**ThoughtSpot**
- **Spotter for Industries** (Mar 19) — sector-tuned versions of the Spotter agent (healthcare, retail/CPG, financial services, tech, supply chain, media/telecom) with industry-specific terminology, connectors, and a bring-your-own-LLM option, positioned as closing a "context gap" where generic NL agents miss sector-specific rules. [Source](https://itbrief.co.uk/story/thoughtspot-unveils-spotter-ai-agents-tailored-by-sector)

**Microsoft**
- **Copilot in web modeling** (Preview, Jun) — conversational editing of Power BI semantic models: renaming fields, building relationships, generating DAX measures via natural language instead of manual edits.

**Industry**
- **Gartner: >50% of enterprise analytics queries expected via natural language/search/voice by end of 2026** — rather than built through drag-and-drop BI interfaces, cited widely across vendor and analyst coverage this year as the headline adoption stat for the category.
