---
title: Updates
tags:
  - market-landscape
  - changelog
---

# Ask Your Data — Market Landscape Update Log

Running log of confirmed developments across the broader natural-language-to-data market — every vendor and open-source project outside Databricks (which has its own log, see [[Databricks/Updates|Databricks Updates]]). Newest entries first.

## 2026-08-10 (second run)

_No genuinely new items beyond the first run today. Rechecked ThoughtSpot (still Cloud Release 26.7.0, same three Early Access items already logged below), Snowflake CoWork/Cortex Analyst, Sigma, Microsoft Copilot for Power BI/Fabric, Amazon Quick, Hex/Omni/Cube/AtScale/WrenAI, dbt Semantic Layer/OSI, Salesforce Tableau Next/Agentforce, and Gartner conversational-analytics coverage — everything resurfaced either matches this log already or pre-dates it with nothing new since. Salesforce's "Tableau Einstein Alliance" partner program surfaced but is a channel/partner initiative, not a product update, so left out._

## 2026-08-10

**ThoughtSpot**
- **Cloud Release 26.7.0 — three new Early Access features** (as of this run) — **Spotter User-Level Personalisation**: Spotter now builds memory from an individual user's own conversations and adapts to their preferences, distinct from the org-wide Genie-Ontology-style context already covered elsewhere. **SpotterViz for Embedded Liveboards**: SpotterViz (the viz-generation agent) can now be embedded directly into smart dashboards so end users build/edit/explore decision-ready dashboards inline. **SpotterCode in Visual Embed Playground**: SpotterCode (ThoughtSpot's coding agent) is now available inside the Visual Embed Playground for building/testing/deploying embedded apps. None of these were previously logged; the prior Spotter Semantics/Spotter for Industries/Gartner Leader entries are unrelated capabilities. [Source](https://www.thoughtspot.com/new-features)

**Metabase** (backfilled — first entry for this vendor in this log)
- **Metabase 63** (Jul 2026) — added more LLM provider options for Metabot (OpenAI, AWS Bedrock, Microsoft Azure, alongside existing providers), plus treemaps, two-factor auth, PDF dashboard-subscription attachments, and one-step dashboard sharing. Flagged here mainly for the Metabot provider expansion, which is the NL-query-relevant piece. [Source](https://www.metabase.com/releases)

_Note: this run also checked Snowflake CoWork/Cortex, Sigma, Hex, Omni, Cube, AtScale, WrenAI, Vanna AI, Google Cloud Conversational Analytics, Amazon Quick, Power BI/Fabric, and Tableau Next/Agentforce — all resurfaced only already-logged material (Snowflake's June Summit CoWork bundle, Hex's Jul 30 CLI/API release already covered, Google Cloud's Jul 29 GA already covered, etc.) or pre-dated this log's baseline with nothing new since. IBM watsonx.data Text2SQL surfaced but its launch traces to November 2025 — too old to count as a delta and not previously logged, so left out rather than backfilled given the age. Might be worth a dedicated ThoughtSpot concept note given how much is accumulating in this log for it — flagging rather than creating one, per this section's scope._

## 2026-08-09

**ThoughtSpot**
- **Named a Leader in the 2026 Gartner Magic Quadrant for Analytics and BI Platforms** (Jul 1) — Gartner specifically cited ThoughtSpot's conversational analytics, external semantic-layer connectivity, and agent workflow orchestration as strengths. [Source](https://www.globenewswire.com/news-release/2026/07/01/3320829/0/en/thoughtspot-named-a-leader-in-the-2026-gartner-magic-quadrant-for-analytics-and-bi-platforms.html)

**Snowflake**
- **Snowflake Intelligence renamed Snowflake CoWork; Cortex Code renamed Snowflake CoCo** (Snowflake Summit, Jun) — a positioning shift, not just a name change: CoWork is pitched as a "colleague" that participates in workflows rather than a BI assistant. Bundled with a push toward GA for Skills (natural-language workflow automation), MCP connectors (Google Workspace, Jira, Salesforce, Slack), Deep Research, a mobile app, and reusable artifacts. Note for future searches: use "Snowflake CoWork," not "Snowflake Intelligence," going forward. [Source](https://www.constellationr.com/insights/news/snowflake-rolls-out-snowflake-intelligence-cortex-code-updates)

**Hex**
- **Hex Agent now accessible via CLI and API** (Jul 30) — previously notebook/browser-only; agent conversations can now run from external tools and scripts. Also ships visibility into which resources the agent used per step, an upgrade to Claude Opus 5, and up to 10x faster Snowflake schema refreshes (incremental fetch instead of full warehouse rescans). [Source](https://learn.hex.tech/changelog/2026-07-30)

**Microsoft**
- **Fabric Skills for GitHub Copilot, Claude, and CLI** (Build 2026, Jun) — open-source toolkit, distinct from the previously-logged Copilot in web modeling, that lets AI coding agents directly author/query Power BI semantic models and other Fabric assets (SQL warehouse, Lakehouse, Eventhouse, Dataflows Gen2). Microsoft built it and opened it to community contribution. [Source](https://community.fabric.microsoft.com/t5/Fabric-Updates-Blog/Fabric-Skills-for-GitHub-Copilot-Claude-and-CLI-built-by/ba-p/5190188)
- **Power BI's "chat with your data" consolidating into Microsoft 365 Copilot** (announced Jul 21, updated Aug 7) — Power BI data is now directly queryable from Microsoft 365 Copilot Chat (preview): ask a business question there and get an answer computed against the governed semantic model, without opening Power BI. Deeper multi-step analysis/automation goes through the pay-per-use Copilot Cowork instead. Strategically, Microsoft is folding the standalone Power BI Copilot (preview) into the M365 Copilot experience rather than growing it separately — positioned as fixing "too many Copilots" confusion. The in-app Report Copilot (GA) stays and will be updated to use the same underlying data-answering tools. Distinct from the Jun "Copilot in web modeling" (semantic-model editing) and the Build 2026 "Fabric Skills" (agent tooling) already logged above — this is about where end users go to ask questions, not how models get built. [Source](https://community.fabric.microsoft.com/t5/Power-BI-Updates-Blog/Bringing-Power-BI-Insights-to-Every-Copilot-User/ba-p/5309360)

**Amazon**
- **Amazon Q Business closes to new customers** (Jul 31) — existing customers keep support and bug fixes but no new features; AWS is directing new generative-BI and agentic-AI workloads to Amazon Quick (the QuickSight-descended suite) instead. [Source](https://docs.aws.amazon.com/amazonq/latest/qbusiness-ug/qbusiness-availability-change.html)
- **Amazon Quick multi-dataset topics now GA** (Aug 6) — a topic (Quick's semantic-model construct) can now span multiple datasets: users define relationships once and Quick performs joins at query time, for both dashboard building and natural-language Q&A. Previously required manually pre-joining data into a single dataset first. Existing row/column-level security carries through automatically. [Source](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-quick/)

**Tableau (Salesforce)**
- **Einstein Copilot for Tableau renamed Tableau Agent** — positioning shift bundling Tableau's AI assistant more tightly under the Tableau brand rather than Einstein's. Tableau Pulse also added automatic threshold alerts (web/email/mobile) when tracked metrics cross defined ranges, and Semantic Search now lets users find dashboards/data sources by business concept rather than requiring exact keyword matches. First entry for Tableau in this log — no prior baseline to delta against. [Source](https://www.tableau.com/blog/tableau-metrics-and-natural-language-query-evolve-tableau-pulse)

**Open source**
- **MindsDB Anton** (launched Apr 2) — open-source autonomous BI agent (Apache-licensed) that turns plain-language questions directly into tables, charts, and dashboards in one pass. Ships with enterprise-oriented governance (credential vault, isolated execution environment, audit trail) and multi-layered memory that lets it retain organizational context and improve over time under analyst oversight. Single-command install (macOS/Linux/Windows), no subscription required. [Source](https://mindsdb.com/newsroom/mindsdb-launches-anton-an-autonomous-open-source-bi-agent)
- **Vanna AI 2.0** (Mar) — MIT-licensed open-source text-to-SQL framework; 2.0 adds local-LLM support via Ollama (no cloud dependency required) and a built-in production-ready web UI. ~22k GitHub stars. Distinct architectural bet from ThoughtSpot/WrenAI-style semantic-layer approaches: Vanna leans on retrieval-augmented example curation rather than an explicit business-logic model. Neither MindsDB Anton nor Vanna had been logged here before — both are backfilled now rather than being a same-week delta.

_Note: Google Cloud Conversational Analytics GA (Jul 29), Gartner's >50% natural-language-query stat, and Sigma's Ask Sigma/MCP-for-ChatGPT rollout were all resurfaced by this run's search but are already logged in the 2026-08-08 entry below with no meaningful delta — not re-added. ThoughtSpot Spotter Semantics (Mar 16) and Spotter for Industries (Mar 19, already logged) also resurfaced but are old ground. A second pass this same day (vault reconnected mid-session after an earlier lapse) added the Amazon Quick, Tableau, and open-source items above, which the first pass — done without vault access — couldn't check against this log and so had flagged in chat as unconfirmed-dedup. A Gartner stat that 90% of analytics content consumers will become creators by end of 2026 also resurfaced but was judged too close to the >50% NL-query stat already logged to warrant a separate line. A third pass this same day added the Power BI/M365 Copilot item above; targeted checks on ThoughtSpot, Snowflake, Cube, AtScale, WrenAI, Omni, and Metabase turned up nothing genuinely new beyond what's already logged._

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
