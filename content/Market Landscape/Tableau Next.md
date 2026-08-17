---
title: Tableau Next
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Salesforce]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

Tableau Next is Salesforce's agentic analytics platform — a rebuild of Tableau on top of Salesforce Data Cloud and Agentforce, unveiled at Tableau Conference 2026 (May 2026) and shipped through a monthly release train since. It bundles **Tableau Agent** (conversational analytics: NL Q&A, chart/dashboard generation from a conversation, agentic data monitoring), **Tableau Semantics** (an AI-ready semantic-model layer, successor to classic Tableau data sources, with plain-language model authoring), and **Tableau Pulse** (the metrics/insights surface, now embeddable directly in Salesforce via Lightning Web Components) into a single agentic-first product line that runs alongside — rather than replacing — classic Tableau Desktop/Cloud/Server. The "Tableau Agent" brand also now reaches into classic Tableau (Tableau Agent in Pulse, Tableau Agent in Dashboards), so it functions as Salesforce's umbrella conversational-analytics layer across both the legacy and Next product lines.

## Core Capabilities

- **Tableau Agent — Data Connection and Analytics Creation** (Beta, Aug 2026) — goes from data discovery to a semantic model to a first visualization in one conversation; automatically locates semantic models, enriches data relationships, and generates editable visual assets
- **Tableau Semantics: Auto Semantic Model Creation** (Beta) — AI generates semantic models, relationships, and calculated fields from plain-language descriptions
- **Semantic Model Builder — Smart Canvas** (GA, Aug 2026) — auto-arranging canvas for authoring/exploring semantic models at enterprise scale
- **Agentic Data Monitoring** (GA, Aug 2026) — verify data-asset freshness and workspace status using natural-language questions instead of manual checks
- **C360 Semantic Model — AI-Ready Verified Questions & Business Preferences** (GA, Aug 2026) — pre-verified cross-cloud questions and built-in business logic for Sales/Service/Marketing, so Tableau Agent gives accurate answers out of the box
- **Tableau Next MCP** — exposes Tableau Next's dashboards, semantic modeling, and alerting to external AI agents (Claude, ChatGPT, Codex, Slackbot) via MCP; "Authoring" reached Beta in Aug 2026, following a Slackbot-via-MCP integration that shipped in July
- **Tableau Agent in Pulse** (classic Tableau, not Next) — now running on GPT‑5.2 with a 400K-token context window (GA, Jul 2026) for sharper multi-part question handling
- **Tableau Agent in Dashboards: Conversational Analytics** (Beta/Pilot, Jul 2026) — ask plain-language questions directly against a dashboard's underlying data source

## Status and History

- Unveiled at Tableau Conference 2026 (May 2026) as part of Salesforce's "Agentic Analytics Platform" push spanning Tableau Cloud, Server, Desktop, and Next
- Shipping on a monthly release train; capabilities have moved from Beta to GA in successive releases (May → Aug 2026)
- **Not previously tracked in this vault** — earlier log entries (2026-08-13/14) surfaced "Salesforce Tableau Next/Einstein Agentic Analytics Platform" activity but dismissed it as stale May-2026 conference news without creating a note. This entry is a backfill correcting that gap; it is explicitly in this skill's scope ("Salesforce Einstein Analytics/Tableau Next").

## Market Position

Salesforce's answer to platform-native conversational-BI/agentic-analytics plays like [[Snowflake CoWork]], [[Sigma]], and [[ThoughtSpot Spotter]] — distinguished by being built directly on Salesforce Data Cloud/Agentforce, so it inherits Salesforce's own object model (Sales/Service/Marketing) and ships pre-verified questions tuned to that data out of the box. Also positions Tableau's classic conversational layer (Tableau Agent in Pulse/Dashboards) as a bridge product for customers not yet on Next.

## Recent Developments

**2026-08-17** — First coverage in this vault (backfill). August 2026 monthly release reached GA on several Tableau Next capabilities — Agentic Data Monitoring, C360 Semantic Model Verified Questions & Business Preferences, Semantic Model Builder Smart Canvas, and a conversationally-guided Admin Home & Settings experience — while Tableau Agent - Data Connection and Analytics Creation and Tableau Next MCP: Authoring both reached Beta. [Source](https://www.tableau.com/products/new-features)

## Related

- [[Snowflake CoWork]] — competing platform-native personal work agent
- [[Sigma]] — competing warehouse-native conversational/agentic BI layer
- [[ThoughtSpot Spotter]] — comparable independent conversational-analytics vendor
- [[Semantic Layer]] — the architectural pattern Tableau Semantics implements; Salesforce is a named backer of the Open Semantic Interchange (OSI) spec
- [[Amazon Quick Suite]] — another platform vendor's expansion of a BI product into a broader NL work-agent suite
- [[MCP]] — Tableau Next MCP is part of the same pattern of BI vendors exposing themselves as MCP endpoints for external AI agents
