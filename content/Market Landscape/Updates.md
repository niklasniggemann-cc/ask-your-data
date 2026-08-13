---
title: Updates
tags:
  - market-landscape
  - changelog
---

# Ask-Your-Data / NL-BI Market Landscape — Update Log

Running log of confirmed developments across the broader natural-language-to-data market (excluding Databricks, which has its own log — see [[Databricks/Updates|Databricks Updates]]). Newest entries first.

## 2026-08-13

_Checked Snowflake (Cortex Analyst/Intelligence/Code docs and release notes), ThoughtSpot Spotter docs, Microsoft Fabric/Power BI Copilot community blog, Sigma release notes (Aug 7 post already assessed as UI polish, not re-logged), Omni, Metabase, dbt Semantic Layer/Cube/AtScale, and OSS text-to-SQL projects (WrenAI, Vanna AI/DataChat) for the Aug 12–13 window — nothing new there. Two vendors this skill's scope covers but this vault had never actually researched turned up real, if not same-day, coverage gaps: Google Cloud (Looker/BigQuery Conversational Analytics) and Microsoft Fabric IQ. Both get first-coverage backfill entries below rather than same-day deltas. Also found one genuine same-day delta each for Hex and Looker._

**Google Cloud — Looker / BigQuery Conversational Analytics** (backfilled — first coverage in this vault)
- **Conversational Analytics API reached GA for BigQuery and Looker** (Jun 23, 2026), with agent-to-agent (A2A) protocol support in Preview and enterprise controls (CMEK, VPC Service Controls, data residency). Google's NL-query layer for Looker/BigQuery — comparable in role to [[Genie Agents]] — had never been tracked in this vault despite being explicitly in scope. New note created: [[Looker Conversational Analytics]]. [Source](https://docs.cloud.google.com/gemini/data-agents/conversational-analytics-api/release-notes)
- **Delta since GA** (Aug 3–7, 2026, Looker 26.12 rollout) — Conversational Analytics data agents published to Gemini Enterprise now render charts/visualizations inline (previously text/table only); query timeout raised from 2 to 5 minutes; editors can toggle whether the agent shows its thinking/debug steps. Updates [[Looker Conversational Analytics]]. [Source](https://cloud.google.com/blog/products/business-intelligence/looker-updates-for-agentic-bi-at-next26)

**Microsoft — Fabric IQ** (backfilled — first coverage in this vault)
- **Fabric IQ reached GA** (Jun 2, 2026, Build 2026) — Microsoft's shared context/semantic layer for AI agents, built directly on existing Power BI semantic models. Functionally the closest Microsoft analogue to [[Genie Ontology]]. A **Fabric IQ plugin for Microsoft 365 Copilot Cowork** (Preview) lets a Cowork chat ground itself in a specific Power BI report by name, using the same permissions and semantic model the user already sees. Ontologies (a further layer above semantic models) are planned but not yet GA. New note created: [[Fabric IQ]]. [Source](https://community.fabric.microsoft.com/t5/Fabric-Updates-Blog/Fabric-IQ-The-shared-context-layer-for-AI-agents-and-real-time/ba-p/5191678)

**Hex**
- **Notebook Agent tuning controls** (Aug 10) — "fast mode" pushes Opus models to 2.5x faster token output at increased usage cost; GPT-5.6 Sol/Terra/Luna added to the model picker (complex/balanced/fast-cheap tiers); new threads default to Endorsed Mode (governed data only) unless an admin disables the enforcement; Auto-picked model is now visible in Context Studio. Incremental agent-tuning/governance polish rather than a new capability class. [Source](https://learn.hex.tech/changelog/2026-08-10)

_Note: also checked "The Future of Data Analytics" (Databricks blog, Aug 12) and general conversational-BI adoption-stat pieces circulating in search results — one Gartner "50%+ of analytics queries via NL by end of 2026" stat traces back to a 2024 survey/2025 report, not new, dropped. Salesforce Tableau Next/Einstein Agentic Analytics Platform activity found was all May 2026 (Tableau Conference) or earlier, already stale relative to any baseline; nothing dated Aug 2026 surfaced. ThoughtSpot's own community news page failed to render (client-side app); relied on the Jul 1 Gartner MQ entry and Jul 28 Cloud 26.7.0 release notes already logged as the current baseline — no indication of anything newer._

## 2026-08-12 (second run)

_Delta-only, checked against the same-day entry below. One backfilled item found — not dated today, but not previously logged in this vault._

**Snowflake — CoWork (rebrand of Snowflake Intelligence)**
- **Snowflake CoWork** (announced Jun 2, 2026 at Snowflake Summit 26; not previously logged here) — a full rebrand and expansion of Snowflake Intelligence into a "personal work agent": CoCo answers questions over governed Snowflake data (the existing Cortex Analyst-style layer), while CoWork sits above it and takes multi-step action — Deep Research reports, published dashboards ("Artifacts"), and actions across Gmail/Slack/Salesforce in natural language. Snowflake claims Cortex Sense (a context-enrichment layer) lifts accuracy on complex queries from 47% to 83%. Repositions Snowflake's ask-your-data surface as a general work assistant, moving it closer to Microsoft Copilot's scope than to narrower conversational-BI tools. New note created: [[Snowflake CoWork]]. [Source](https://www.snowflake.com/en/news/press-releases/snowflake-cowork-powers-the-agentic-enterprise-as-the-personal-agent-for-knowledge-workers-to-work-smarter/)

_Note: also checked ThoughtSpot's release notes (Cloud 26.7.0, last updated Jul 28) — Spotter user-level personalization/memory and SpotterViz embedded-liveboards are both still Early Access, already directionally covered by the Aug 11 entry, not a distinct delta. Checked Sigma, Omni, Hex, Metabase, dbt Semantic Layer/Cube/AtScale, and OSS text-to-SQL projects — nothing new. An IBM watsonx.data "Text2SQL" result surfaced in search but its actual launch was November 2025, predating this vault's coverage window — not a delta, dropped._

## 2026-08-12

_No genuinely new items today. Checked Microsoft Fabric/Power BI Copilot community blog, Snowflake Cortex Analyst/Intelligence/Cortex Code docs and release notes, ThoughtSpot Spotter docs, Sigma Computing's weekly release notes (Aug 7 post is UI polish — new "Drawers" component and a Snowflake-usage-monitoring template — not NL-BI relevant), Omni, Hex, Metabase, dbt Semantic Layer/Cube/AtScale, and OSS text-to-SQL projects (WrenAI, Vanna AI forks, DataChat) for the Aug 11–12 window. Nothing confirmed, dated, non-financial, and genuinely new against the baseline below surfaced — mostly recycled comparison/listicle content ("best BI tools 2026" roundups) rather than actual releases._

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
