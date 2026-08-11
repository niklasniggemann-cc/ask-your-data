---
title: Updates
tags:
  - market-landscape
  - changelog
---

# Ask-Your-Data / NL-BI Market Landscape — Update Log

Running log of confirmed developments across the broader natural-language-to-data market (excluding Databricks, which has its own log — see [[Databricks/Updates|Databricks Updates]]). Newest entries first.

## 2026-08-11

_First run for this project — no prior baseline, so this entry is broader than a typical daily delta, similar to the Databricks log's first run. Expect future entries to be much shorter, delta-only updates. Financial framing (funding rounds, valuations) dropped per scope even where it was the vehicle for a real product announcement._

**Microsoft — Copilot for Power BI / Fabric**
- **Copilot Chat can now query Power BI data directly** (~Aug 8) — any Microsoft 365 Copilot user can ask a plain-English business question ("What was revenue last week?") in Copilot Chat and get a grounded answer computed against the governed Power BI semantic model, without opening Power BI or building a report first. Requires an M365 Copilot license. This is Microsoft's most direct answer yet to "ask your data from anywhere," extending Power BI's semantic layer beyond the Power BI app itself. [Source](https://community.fabric.microsoft.com/t5/Power-BI-Updates-Blog/Bringing-Power-BI-Insights-to-Every-Copilot-User/ba-p/5309360)
- **Copilot in web modeling** (Preview) — a natural-language assistant inside the Power BI semantic-model editor that flags issues (inconsistent naming, unclear structure) and can execute schema changes itself: renaming tables/columns, creating relationships, generating DAX measures. Moves Copilot from "ask questions about data" into "edit the semantic layer via chat." [Source](https://community.fabric.microsoft.com/t5/Power-BI-Updates-Blog/Copilot-in-web-modeling-Preview/ba-p/5182287)

**Snowflake — Cortex Analyst / Cortex Code / Snowflake Intelligence**
- **AI code suggestions in Workspaces now GA** (Jul 28) — the latest step in Cortex Code's rollout (CLI GA Feb 2, Snowsight GA Mar 9), extending inline AI-assisted SQL/Python authoring across Snowflake's own workspaces. Snowflake continues positioning Snowflake Intelligence + Cortex Code as a single control plane for both natural-language business questions (Cortex Analyst/Intelligence) and AI-assisted data engineering (Cortex Code) — Agent Teams (coordinated parallel agent work) also shipped as part of this push. [Source](https://docs.snowflake.com/en/release-notes/2026/other/2026-07-28-cortex-code-ai-suggestions-ga)

**ThoughtSpot — Spotter**
- **Named a Leader in the 2026 Gartner® Magic Quadrant™ for Analytics and BI Platforms** (Jul 1) — one of the only independent (non-hyperscaler-owned) vendors in the Leaders quadrant. Gartner specifically cited three strengths: conversational analytics through Spotter, external semantic-layer connectivity, and agent workflow orchestration — a notable analyst endorsement of the conversational-BI category itself, not just ThoughtSpot. New note created: [[ThoughtSpot Spotter]]. [Source](https://www.thoughtspot.com/data-trends/2026-gartner-magic-quadrant-for-analytics-and-business-intelligence)
- **Spotter now runs on SpotQL**, a semantic query engine built to handle nested logic, comparative rankings, derived metrics, and multi-step filtering — addressing a common complaint that first-generation NL-to-SQL tools handle simple lookups well but fail on genuinely multi-step analytical questions. [Source](https://www.techtarget.com/searchbusinessanalytics/news/366636078/ThoughtSpot-automates-full-platform-with-new-Spotter-agents)

**Sigma Computing**
- **Sigma MCP Server** — Sigma now supports MCP as both client and server: MCP Client lets Sigma's Ask Sigma / AI Builder pull context from tools like Google Drive, Confluence, and GitHub; MCP Server exposes Sigma's own data and admin operations to external agents in Claude, ChatGPT, or internal chat tools, with Sigma's existing account-, connection-, column-, and row-level security enforced across every AI assistant. Part of a broader industry pattern of BI vendors exposing themselves as MCP servers (see also Databricks' Genie One MCP server, logged separately). [Source](https://www.sigmacomputing.com/blog/sigma-mcp-server-ai-assistants)

**Omni**
- **AI Hub** (June) — a new command center giving teams one place to observe how AI features are actually being used, improve the underlying semantic model based on that usage, and validate changes before they ship to production. Positions semantic-model quality management as its own discrete AI-era workflow rather than a one-time setup task.

**Metabase**
- **Metabot AI provider flexibility** (v63, July) — Metabot now supports OpenAI, AWS Bedrock, and Azure as pluggable LLM providers, so customers can point Metabot at an AI provider they already have a contract/compliance relationship with instead of a fixed default.

**OSS / Semantic Layer**
- **WrenAI repo consolidation** (May 7) — the open-source `wren-engine` was merged into the main `Canner/WrenAI` repository under `core/`; the prior Docker-based chat-first GenBI app is preserved on a `legacy/v1` branch as "Wren GenBI Classic." Mostly an engineering/maintenance move, noted here as a marker of where the project is putting its development weight (the engine/context-layer core, not the standalone chat app).

_Note: checked Reddit (r/BusinessIntelligence, r/dataengineering), Hacker News, and general vendor blog searches for Cube, AtScale, dbt Semantic Layer, Looker/Google Cloud conversational analytics, Amazon Q in QuickSight, Tableau Pulse, and DataChat/Vanna AI/Seek AI — no confirmed, dated, non-financial product news surfaced for the Aug 2026 window specifically; existing coverage found was either older (pre-July) or pure market-positioning content (e.g. "best semantic layer" comparison articles) rather than an actual shipped feature, so left out per the confirmed-and-new filter._
