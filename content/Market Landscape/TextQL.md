---
title: TextQL
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[TextQL]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

TextQL is an AI-analyst platform built around **Ana**, an agent that answers business questions in natural language over an enterprise's existing data estate (warehouses, BI tools, operational apps, APIs) without requiring a prior centralization or migration project. Its differentiator is the **Ontology**: a self-maintaining semantic layer that Ana builds by reading schemas, relationships, query logs, and business logic across connected systems, then stores as a plain, Git-backed file tree the customer owns outright rather than a proprietary model locked inside a vendor's platform. Backed by customers including Blackstone, Dropbox, Scale AI, and the NBA; categorized by Gartner under the emerging "agentic analytics" market.

## Core Capabilities

- **Ana** — the AI analyst agent: takes a plain-language business question, generates SQL/Python, produces visualizations, and can run automated workflows; reachable via chat, Slack/Teams/email, or headless through any MCP client (Claude, ChatGPT, custom agents)
- **Ontology** — a self-maintaining semantic layer assembled automatically from connected systems (schemas, field definitions, query logs, business logic), stored as version-controlled files synced bidirectionally with a Git remote on the customer's own account rather than living only inside TextQL's platform
- **TQL** — TextQL's query file format: a SQL query annotated with an English description, parameters, and the governance/permissions that guard it, so both a human and any AI agent can read the same file and get the same meaning
- **Self-extending definitions** — every question Ana answers can surface a proposed patch to the Ontology (e.g. refining a metric definition after repeated analyses hit the same gap); patches are reviewable and require approval before merging
- **Data Apps, Agents, Actions** — beyond read-only Q&A, the Ontology also stores data apps, saved agents (e.g. scheduled anomaly-watch agents), and permissioned write actions (writing to a warehouse, calling an API), all governed by the same model that defines what a metric means
- **Connectors** — reads across cloud data platforms (Snowflake, Databricks, Postgres), BI tools (Tableau), and operational apps (Salesforce) without requiring the data to move first

## Market Position

Sits in the "AI analyst" segment of NL-BI alongside Seek AI, DataChat, and Vanna AI, but distinguishes itself with the Ontology's customer-owned, Git-native storage model — positioned explicitly against vendors whose semantic layer is "readable only through them." Headless design lets it plug into Claude, ChatGPT, or a customer's own agent harness rather than requiring adoption of a TextQL-branded chat surface. Not previously covered in this vault despite being explicitly in scope ("text-to-SQL startups... Seek AI, DataChat, Vanna AI, WrenAI, etc.") — a coverage gap similar to prior backfills of Amazon Quick Suite, Fabric IQ, and Looker Conversational Analytics.

## Related

- [[Semantic Layer]] — the Ontology is TextQL's specific implementation of a semantic layer, notable for being Git-native and customer-owned by design
- [[Natural Language to SQL]] — Ana's core answer-generation mechanism, grounded by the Ontology rather than operating on raw tables
- [[MCP]] — Ana is reachable headlessly through any MCP client, part of the broader pattern of NL-BI vendors exposing themselves over MCP
- [[Sigma]] — another vendor whose agents ground themselves in a governed semantic model rather than raw tables, though Sigma's model lives inside its own platform rather than a customer-owned Git repo
