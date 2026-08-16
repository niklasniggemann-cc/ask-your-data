---
title: Genie One
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Unified AI Chat Interface
tags:
  - genie
  - databricks
---

## Definition

Genie One is the unified full-screen chat experience for [[Databricks]] business users. It acts as a single entry point that searches across all published [[Genie Agents]], dashboards, queries, and metric views — eliminating the need to know which specific agent to open.

## Core Capabilities

- Searches across Genie Agents, dashboards, queries, and metric views in a single interface
- Schedules recurring chat tasks that post results back as threads
- Generates documents from chat conversations
- Two-way integrations: Gmail, Slack, Microsoft Teams
- Custom skills and custom [[MCP]] connections

## Multi-Platform Access

- **Slack and Microsoft Teams** — invoked via @mention in conversations, public channels, and threads; responses scoped to each user's individual authorisation
- **iOS and Android** mobile client
- **Genie MCP App** — allows organisations running their own AI agents to call Genie without a separate workflow
- **Google Sheets and Microsoft Excel** (Aug 2026) — via the Databricks Connector for Google Sheets and the Databricks Excel Add-in; query governed data in natural language and import results as native rows and columns

## External Sources

Genie One connects to external data sources alongside [[Unity Catalog]] data:
- Google Drive
- SharePoint
- Gmail
- Slack
- Atlassian
- Glean

## Agentic Features

- Multi-step reasoning and hypothesis testing (Agent Mode)
- Creates and refines a research plan
- Runs multiple SQL queries, learns from each, iterates
- Returns comprehensive answers with citations, visualisations, and tables via SSE streaming

## Recent Developments

- **2026-08-06** — **Upload PDF files to a conversation** (Beta): PDFs can now be attached to a Genie One conversation alongside CSV and Excel files, parsed asynchronously. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)
- **2026-08-03** — Databricks published the **Genie One MCP server** (Beta), a managed MCP server at `/api/2.0/mcp/genie` that exposes Genie One itself as a callable tool for any external MCP client or agent (Cursor, Claude Desktop, custom orchestrators). Tools include `genie_ask`, `genie_poll_response`, `genie_get_query_result`, `genie_cancel_response`, and `view_ask` for MCP Apps clients (interactive inline View with charts and citations). Answers are grounded in Genie Ontology with Unity Catalog permissions enforced. Requires the Managed MCP Servers workspace preview. [Source](https://docs.databricks.com/aws/en/agents/mcp-tools/genie-mcp)

## Related

- [[Genie Agents]] — the curated domain-specific agents Genie One searches across
- [[Genie Ontology]] — the org-wide context layer that feeds all Genie One responses with shared business meaning
- [[Genie Code]] — developer-focused counterpart
- [[Genie App Builder]] — sibling Genie-family product for building governed data apps rather than chatting over data
- [[Genie ZeroOps]] — sibling Genie-family product for autonomous data/AI operations
- [[Databricks]] — platform
- [[ThoughtSpot Spotter]] — comparable unified conversational-analytics surface on ThoughtSpot
- [[Amazon Quick Suite]] — AWS's comparable evolution of QuickSight into a broader natural-language work-agent platform
- [[MCP]] — supports custom MCP connections and is itself exposed as an MCP server
