---
title: Snowflake CoWork
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Snowflake]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

Snowflake CoWork is Snowflake's personal AI work agent for knowledge workers — a full rebrand and expansion of the earlier "Snowflake Intelligence" product, announced June 2, 2026 at Snowflake Summit 26. Where the Cortex Analyst / Snowflake Intelligence framing centered on "ask a question about governed data, get an answer," CoWork repositions the product around *taking action*: it reasons across multi-step tasks, automates routine work, and carries a business question through to a decision and an executed action, not just a chat answer.

## Core Capabilities

- **CoWork itself is the NL Q&A + action layer** — a user's question routes through the Cortex Agent API, which uses Cortex Analyst (NL-to-SQL over semantic views) and Cortex Search (unstructured data) as tools, then CoWork's own layer runs multi-step Deep Research reports, publishes interactive governed dashboards ("Artifacts"), and takes actions across external tools like Gmail, Slack, and Salesforce in natural language
- **Cortex Sense** — a context-enrichment layer Snowflake says lifts accuracy on complex enterprise queries from 47% to 83% when paired with CoWork
- **Domain Agents** — pre-scoped agents for specific business domains, generally available alongside the core chat interface at ai.snowflake.com
- Personalization features layered on top of the existing Cortex Analyst / Cortex Agents / Cortex Search stack

## Market Position

Positions Snowflake's "ask your data" surface as a general-purpose agentic work assistant rather than a narrower BI chat feature, putting it in more direct competition with Microsoft Copilot (which spans Power BI and the rest of M365) than with narrower conversational-BI tools like [[ThoughtSpot Spotter]]. The rebrand had already happened by June 2026 but had not been captured in this vault's dedicated Snowflake coverage until this entry.

## Recent Developments

**2026-08-20 (Preview)** — **Cortex Agent code execution tool**: a built-in tool letting a Cortex Agent run Python in a sandboxed, session-scoped environment (process data, calculations, visualizations), alongside its existing Cortex Analyst/Cortex Search tools rather than replacing them — the agent still uses SQL tools for data retrieval, then hands results to the sandbox. Distinct from and mutually exclusive with `code_toolset_all`, the full CoCo (Cortex Code) developer-agent toolset. Extends what a Cortex Agent — and by extension CoWork's Q&A layer — can do with a data answer beyond returning a table. [Source](https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-agents-code-execution-tool)

**2026-07-07** — Deep Research in Snowflake CoWork reached GA, moving CoWork's multi-step research reports out of preview. [Source](https://docs.snowflake.com/en/release-notes/2026/other/2026-07-07-snowflake-cowork-deep-research-ga)

**2026-08-06** — Automations (Public Preview): CoWork can now re-run a saved question on a schedule with fresh data and email a summary plus a link back into the full interactive report, turning a one-time report into a recurring one. [Source](https://docs.snowflake.com/en/release-notes/2026/other/2026-08-06-cowork-automations)

**2026-08-07** — Cortex Agents and MCP servers can now be packaged and distributed as Snowflake Native Apps (GA), including Snowflake-managed MCP servers exposing an app's Cortex Search services/semantic views/procedures as tools, and inter-app agent-to-agent calls — a governed conversational agent becomes an installable Marketplace app rather than a bespoke integration. [Source](https://docs.snowflake.com/en/release-notes/2026/other/2026-08-07-native-apps-agents-mcp-ga)

**2026-08-18 (correction)** — Earlier entries in this note described "CoCo" as CoWork's underlying data-answering layer. That was wrong: **CoCo is the new name for Cortex Code** (renamed by Aug 2026), a separate AI *coding* agent for engineers/data teams (pipelines, dbt, ML, semantic-view authoring), distinct from CoWork's own NL Q&A layer for business users. CoWork's chat interface itself routes directly to the Cortex Agent API (which calls Cortex Analyst/Cortex Search as tools) — no CoCo involved. The two products share the same underlying models (Claude, GPT) and a common "agentic control plane" positioning, but serve different personas: CoCo for people who write code, CoWork for people who ask questions. Corrected here and on [[Semantic Layer]]. [Source](https://www.snowflake.com/en/product/snowflake-coco/) / [Source](https://docs.snowflake.com/en/user-guide/snowflake-cortex/snowflake-cowork)

## Related

- [[Genie One]] — Databricks' equivalent unified chat surface across agents and external sources; similar ambition to unify "ask" and "act"
- [[ThoughtSpot Spotter]] — a narrower conversational-analytics agent by comparison, without CoWork's action-taking scope
- [[Looker Conversational Analytics]] — Google Cloud's competing conversational layer, narrower in scope (Q&A/visualization vs. CoWork's action-taking)
- [[Fabric IQ]] — Microsoft's competing context layer, feeding Copilot Cowork rather than a Snowflake-native chat surface
- [[Sigma]] — a warehouse-native BI layer that sits on top of Snowflake rather than competing as a platform-native chat surface; a Sigma Agent can call Cortex as a tool
- [[Amazon Quick Suite]] — AWS's comparable evolution of QuickSight into a broader natural-language work-agent platform
- [[Natural Language to SQL]] — the underlying technique CoCo's data-answering layer builds on
- [[Semantic Layer]] — the governed-meaning layer CoCo depends on for grounded answers
- [[Tableau Next]] — Salesforce's comparable rebuild of its analytics product into an agentic platform, built on Data Cloud/Agentforce
