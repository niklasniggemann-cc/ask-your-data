---
title: MCP
aliases:
  - Model Context Protocol
type:
  - "[[Technology]]"
  - "[[Standard]]"
created-by: Anthropic
category: Agent-Tool Connectivity Protocol
tags:
  - framework
---

## Definition

MCP (Model Context Protocol) is Anthropic's open standard for connecting AI assistants to external data sources and tools. It defines a client-server protocol where AI models dynamically discover available tools and use them to interact with external systems — without requiring bespoke integration code per tool.

## Key Properties

- **Open standard** — not proprietary; any vendor can implement MCP servers or clients
- **Tool discovery** — clients learn what tools are available at runtime, not at compile time
- **Read-oriented by default** — when used with data sources, queries are typically read-only
- **Stateless connections** — each tool call is self-contained

## How It Works

1. An MCP client (AI agent or application) connects to an MCP server
2. The client queries the server for available tools and their schemas
3. The client invokes tools as needed during reasoning
4. The server executes the tool and returns results

## In the Databricks Context

[[Genie One]] supports custom MCP connections, managed through Unity AI Gateway inside [[Unity Catalog]]. This allows organizations running their own AI agents to call Genie without building a separate workflow.

As of Sep 10, 2026, Databricks also offers a maintained set of **first-party MCP connectors** for Genie One and Genie Code — Google Drive, Gmail, Google Calendar, Microsoft 365, Atlassian, Slack, and GitHub (GA) — so orgs no longer need to build these integrations themselves; each is still governed through Unity Catalog/Unity Gateway with per-user OAuth and audit logging.

Databricks also runs the reverse direction: a **Genie One MCP server** (Beta, `/api/2.0/mcp/genie`) exposes Genie One itself as an MCP tool, so any external MCP client or agent can ask it natural-language data questions and get Ontology-grounded, permission-scoped answers — with an interactive inline View for MCP Apps-compatible clients. See [[Genie One]] for details.

[[MotherDuck]] also exposes an MCP server, making its databases accessible to AI agents via the protocol — the basis of the "Talk to your Data" series.

## Related

- [[Genie One]] — supports custom MCP connections
- [[Agent Bricks]] — Databricks' agent platform; integrates MCP for tool connectivity
- [[Omnigent]] — meta-harness that governs MCP connections at the harness level
- [[Unity Catalog]] — Unity AI Gateway manages MCP connections and costs
- [[OntoBricks]] — exposes a Unity Catalog-derived knowledge graph to agents via an MCP server
- [[Agent Skills]] — complementary open standard for packaging instructions rather than live tool access
- [[MotherDuck]] — exposes an MCP server making its databases accessible to AI agents
