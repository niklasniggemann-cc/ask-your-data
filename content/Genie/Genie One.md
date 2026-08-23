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
- **Google Sheets and Microsoft Excel** (Aug 2026) — via the Databricks Connector for Google Sheets and the Databricks Excel Add-in; query governed data in natural language and import results as native rows and columns. As of Aug 20, 2026 the Google Sheets connector also supports writing data back to a Unity Catalog table (create new or overwrite existing) without leaving the sheet

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

- **2026-08-20** — **Write data back to Databricks from Google Sheets**: the Databricks Connector for Google Sheets now supports writing data from Google Sheets back to a Unity Catalog table (create new or overwrite existing), closing the loop from "ask a question in Sheets via Genie One" to "push the edited result back to the lakehouse." [Source](https://learn.microsoft.com/en-us/azure/databricks/integrations/google-sheets/write-back)
- **2026-08-20** — **Inbound Private Link now supports account-level Genie One** (Beta): enterprises can now put account-level Genie One (plus the account console, Governance Hub, and account-level APIs) behind Inbound Private Link, keeping that traffic off the public internet with the same guarantees already available for workspace resources — including custom-URL support and a single shared endpoint per any region. [Source](https://www.databricks.com/blog/inbound-private-link-now-supports-account-level-genie-one-account-console-and-custom-urls)
- **2026-08-13** — **MCP writes** (Beta): connected MCP tools (Google Drive, Gmail, Microsoft 365, Atlassian, Glean, Slack, GitHub, custom connections) can now perform write actions in the source app, not just search/read — scoped per-user by OAuth consent and the user's own permissions in the source application. [Source](https://docs.databricks.com/aws/en/genie-one/external-sources)
- **2026-08-13** — **Workspace instructions** (GA): admins can define standing instructions (data conventions, terminology, response guidelines) that apply to every chat conversation workspace-wide, via an auto-read Markdown file. Chat only, not Genie Agents or Genie Code. [Source](https://docs.databricks.com/aws/en/genie-one/chat#workspace-instructions)
- **2026-08-13** — **Upload images and Word documents**: conversations now accept PNG/JPG/JPEG and `.docx` files alongside the existing CSV/Excel/PDF support. [Source](https://docs.databricks.com/aws/en/genie-one/chat#upload-a-file)
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
