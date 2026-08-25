---
title: Sigma
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Sigma Computing]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

Sigma is a warehouse-native BI and spreadsheet-interface platform that has expanded into a governed conversational and agentic layer over live warehouse data. Its natural-language surface — **Ask Sigma** / **Sigma Assistant** — answers questions and, increasingly, builds content directly in a workbook, while **Sigma Agents** let teams define reusable, governed AI agents that can call out to warehouse-native tools (including other vendors' agents, like Snowflake Cortex or Databricks Genie spaces) as part of their workflow.

## Core Capabilities

- **Ask Sigma / Sigma Assistant** — natural-language Q&A over governed data, plus (as of July 2026) a "Builder" mode that drafts charts, tables, KPIs, filters, and full apps/forms inside a workbook from a plain-language description rather than only answering questions about existing content
- **Sigma Agents** — reusable, governed AI agents that move through the same dev → production promotion flow as other Sigma content; permissions are enforced through the agent itself, so no user gains access to data just because an agent can reach it
- **Agent Builder Assistant** (July 2026) — drafts a working agent (instructions + tools) from a plain-language description and a connected data source
- **Governed sources for agents** — agents can point at a governed Data Model or a Warehouse Search service instead of raw tables, inheriting existing metric definitions, relationships, and governance rather than requiring an agent-specific redefinition
- **AI Column** (beta, July 2026) — a no-code column that runs a plain-language prompt against one or more columns on every row, returning text or structured JSON; executes through the underlying warehouse's own AI function so data never leaves the platform
- **Workbooks as Code** (preview, July 2026) — every workbook exposed as a versionable spec via the Sigma REST API, aimed at coding agents migrating dashboards off legacy BI tools
- **Sigma MCP Server** (Aug 2026) — Sigma as both MCP client (Ask Sigma/AI Builder pulling context from tools like Google Drive, Confluence, GitHub) and MCP server (exposing Sigma's own data and admin operations to external agents in Claude, ChatGPT, or internal chat tools), with Sigma's existing account/connection/column/row-level security enforced across every AI surface
- **AI usage dashboard** — token consumption, tool calls, model used, and user feedback, broken out by agent and by Assistant, shipped to every customer; paired with cost-monitoring templates tracking spend across Claude, ChatGPT, and Snowflake Cortex AI Functions
- **Sigma CLI** (GA, Aug 2026) — a `sigma` command-line tool for accessing the full Sigma REST API from the terminal (authentication management, typed commands, profile-based configuration), extending Sigma's API surface to AI coding tools and scripts alongside the chat/workbook UI

## Market Position

Positions itself as a warehouse-native alternative to platform-bundled conversational layers ([[Genie Agents]], Cortex Analyst, [[ThoughtSpot Spotter]]): rather than owning the warehouse, Sigma sits on top of Snowflake, Databricks, and others, live-querying rather than syncing data, and lets its agents orchestrate other vendors' native agents (e.g. a Sigma Agent calling a Snowflake Cortex agent or a Databricks Genie space as a tool). Named Databricks' 2026 ISV Business Intelligence Partner of the Year (second year running) and Snowflake's BI Partner of the Year (fourth year running), and recognized in the 2026 Gartner Magic Quadrant for Analytics and Business Intelligence Platforms. Sigma is targeting agents that run outside the workbook on a schedule (not just interactively) by end of Q3 2026.

## Related

- [[Genie Agents]] — Databricks' native equivalent; a Sigma Agent can call a Genie space as a tool rather than replace it
- [[Snowflake CoWork]] — Snowflake's own native conversational/agentic layer, competing directly with Sigma on the same warehouse
- [[ThoughtSpot Spotter]] — a comparable independent, non-hyperscaler-owned conversational-BI vendor
- [[Semantic Layer]] — Sigma Agents ground themselves in governed Data Models, the same architectural pattern as every other vendor in this vault
- [[MCP]] — Sigma's MCP client/server implementation is part of the broader pattern of BI vendors exposing themselves as MCP endpoints
- [[Amazon Quick Suite]] — also ships governed dashboard-migration tooling as part of its own BI-migration play
- [[Tableau Next]] — Salesforce's competing agentic-analytics rebuild of Tableau, built on Data Cloud/Agentforce rather than a live warehouse connection
- [[Market Landscape/TextQL|TextQL]] — another vendor grounding its agent in a governed semantic model, though TextQL's Ontology is stored as a customer-owned Git repo rather than living inside the vendor's own platform
