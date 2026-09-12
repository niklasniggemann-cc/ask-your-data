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
- Generates documents from chat conversations — now editable, commentable, version-tracked, shareable via link, and exportable to PDF or (via MCP writes) into another connected tool (Aug 2026)
- Two-way integrations: Gmail, Slack, Microsoft Teams
- Custom skills and custom [[MCP]] connections

## Multi-Platform Access

- **Slack and Microsoft Teams** — invoked via @mention in conversations, public channels, and threads; responses scoped to each user's individual authorisation
- **iOS and Android** mobile client
- **macOS desktop app** (Beta, Aug 2026) — a native app that opens Genie One outside the browser, inheriting the same IdP/OAuth and governance as the web experience
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

- **2026-09-10** — **Databricks-provided MCP connectors reach GA**: Genie One (and Genie Code) can now use Databricks-provided, first-party MCP connectors for Google Drive, Gmail, Google Calendar, Microsoft 365, Atlassian, Slack, and GitHub — governed through Unity Catalog/Unity Gateway with per-user OAuth, built-in policies, and audit logging — without an org building its own MCP integration. Extends the existing custom-MCP-connection capability into a maintained connector set. [Source](https://docs.databricks.com/aws/en/genie-one/external-sources)
- **2026-09-10** (minor) — **Genie Code skills in Genie One (Beta)**, on by default; **backend steering** (send a steering message while Genie One is still generating a response); **PowerPoint uploads** (`.pptx`); **memory confirmation prompts (Beta)** — Genie One now proactively suggests a memory and asks for approval before saving it, rather than only saving on explicit request. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)
- **2026-09-03** — **Push notifications for scheduled tasks** (Public Preview): the Genie mobile app can now send push notifications to iOS devices when a scheduled task completes. [Source](https://docs.databricks.com/aws/en/genie-one/mobile#push-notifications)
- **2026-09-01** — **Web search** (Beta): Genie One can now search the public web for current information (release notes, third-party docs, news) and cites external sources as links. Requires partner-powered AI features and an eligible geo. [Source](https://docs.databricks.com/aws/en/genie-one/chat#web-search)
- **2026-09-01** — Genie One (and [[Genie Agents]]) can now use models served through **OpenAI on Databricks** when partner-powered AI features are enabled. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/september)
- **2026-07-16** (backfilled) — **Memory** (Beta): Genie One retains specific facts a user explicitly asks it to remember (preferences, workflows, conventions) and applies them automatically in later conversations — private to the user, cited when used, correctable in conversation. [Source](https://docs.databricks.com/aws/en/genie-one/chat#add-to-genie-ones-memory)
- **2026-06-04** (backfilled) — **User skills** (Public Preview): personal, private repeatable tasks a user teaches Genie One once and re-runs on demand (e.g. "build my weekly metrics report"), auto-loaded when relevant or invoked with `/skill-name`. Also shipped same day: **Rich output** (Public Preview) — non-SQL responses (search results, MCP reads) can include rich HTML/CSS/JS instead of plain prose. [Source](https://docs.databricks.com/aws/en/genie-one/chat#user-skills)
- **2026-08-28** — **Document collaboration and agent/chat sharing**: documents generated from a conversation are now editable in place (draft, revise, comment, version history, accept/reject changes), shareable via read-only link, downloadable as PDF, and exportable into another connected tool via MCP writes. Two new ways to make a conversation reusable: create a Genie Agent directly from a conversation (saves it as a reusable, shareable agent), and share a full conversation via read-only link. [Source](https://www.databricks.com/blog/beyond-answers-new-genie-one-features-turn-insights-action)
- **2026-08-27** — **Open Unity Catalog tables directly in Genie**: view a table's overview, columns, and sample data inline next to an ongoing chat, browse a catalog-style table view in Discover, jump straight into "Ask Genie" from a table, or request access if you only have browse rights — no more detour through Catalog Explorer. Also shipped: pin/rename chats in the sidebar, visualizations in scheduled task email outputs, and creating scheduled tasks directly from the Genie mobile app (Public Preview). [Source](https://docs.databricks.com/aws/en/genie-one/#open-tables)
- **2026-08-25/27** — **macOS desktop app reaches Beta**: a native app for chat, threads, documents, and Genie Agents outside the browser — same pattern as the Jul 14 mobile app (no separate backend, inherits the same IdP/OAuth and network/governance controls). Platform release notes date this Aug 25; the AI/BI release notes page groups it under Aug 27 — noted discrepancy between the two official sources. [Source](https://docs.databricks.com/aws/en/genie-one/desktop)
- **2026-08-24** (backfilled, launched Jul 14) — **Genie One mobile app** (Public Preview): native iOS and Android apps bringing the full Genie One experience — chat with skills/MCP support, mobile-optimized dashboards, Databricks Apps — to phones. No separate mobile backend: authenticates through the same IdP/OAuth flow, same URLs, same governance (Unity Catalog, source-native ACLs) as the browser. Follow-up refinements (Aug 20): switch workspaces without signing out; sign in behind account-level IP access lists. Also added: export Genie One documents to PDF (Aug 20). [Source](https://www.databricks.com/blog/take-insights-anywhere-genie-one-mobile)
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
- [[Governance Hub]] — account-level governance product Genie One's agentic insights extend into
- [[ThoughtSpot Spotter]] — comparable unified conversational-analytics surface on ThoughtSpot
- [[Amazon Quick Suite]] — AWS's comparable evolution of QuickSight into a broader natural-language work-agent platform
- [[MCP]] — supports custom MCP connections and is itself exposed as an MCP server
- [[Looker Conversational Analytics]] — Google Cloud's comparable conversational layer, published as a data agent surface
- [[Snowflake CoWork]] — Snowflake's equivalent unified chat surface across agents and external sources
