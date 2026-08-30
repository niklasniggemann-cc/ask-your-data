---
title: Strategy
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Strategy]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
  - semantic-layer
---

## Definition

Strategy (formerly **MicroStrategy**, rebranded 2025) is a 35+ year old enterprise BI vendor that has repositioned itself around **Strategy Mosaic**, a standalone "universal semantic layer" that sits above a customer's existing warehouses and BI tools, plus **Strategy AI Agents** that answer natural-language business questions grounded in Mosaic's governed metric definitions. Distinct from most vendors in this vault by explicitly refusing to be tied to one warehouse or one BI frontend: Mosaic connects to 200+ sources (Snowflake, Databricks, BigQuery, Redshift, SAP, Salesforce, on-prem databases) and serves governed definitions out to any BI tool, AI agent, or application via SQL, DAX, MDX, REST API, or MCP, explicitly marketed against being "trapped" inside a single platform's native semantic layer.

## Core Capabilities

- **Strategy Mosaic** — the universal semantic layer: two modeling paths, **Mosaic Models** (self-service, AI-assisted modeling in Mosaic Studio — auto-detects attributes, hierarchies, and relationships from connected data) and **Mosaic Schema** (centrally governed enterprise semantics — metrics, hierarchies, security policies); Models can map directly to Schema so business teams can build without disrupting governed definitions
- **Strategy AI Agents** — agents grounded in Mosaic's governed metrics rather than raw tables, reachable through third-party AI surfaces (ChatGPT, Claude, Copilot, Gemini) via Mosaic's MCP server, plus native "Strategy Agents"; flat-rate pricing rather than token-based billing, pitched against vendor/model lock-in
- **Long-Term Memory for Agents** (Aug 2026) — agents build persistent memory of a user's preferences (language, framing, recurring concepts) across conversations; users can review and delete stored memory items
- **Mosaic Sentinel** — real-time governance layer monitoring data-access events, flagging anomalies and PII exposure, and maintaining a full audit trail across every human and agent consumer
- **Strategy BI / Library** — the reporting/dashboard layer, including **email bursting** (Aug 2026): one dashboard subscription resolves per-recipient addresses and per-recipient filters from the data itself, generating a full set of personalized deliveries without manual export/slice work
- **HyperIntelligence** — Strategy's older embedded-insight-card feature (contextual data overlays inside other apps), now positioned as part of the broader AI Agents/BI surface

## Market Position

Competes directly with the semantic-layer plays of dbt Semantic Layer, Cube, and AtScale, and markets itself explicitly against being embedded inside a single hyperscaler platform the way [[Genie Agents]] (Databricks) or Cortex Analyst (Snowflake) are — Strategy's pitch is that Mosaic's definitions survive a warehouse or BI-tool migration unchanged. Also positions against AtScale (its closest historical peer, also MDX/DAX-native, OLAP-heritage) by emphasizing Mosaic Sentinel's governance/audit layer as a native rather than bolted-on capability. Ships monthly product-update posts (this vault found no prior coverage despite Strategy/MicroStrategy being a long-established, still-active player explicitly adjacent to this skill's "dbt Semantic Layer and other semantic-layer players" scope) — a coverage gap similar to prior backfills of TextQL and Amazon Quick Suite.

## Related

- [[Semantic Layer]] — Mosaic is Strategy's implementation of a vendor-agnostic semantic layer, in the same architectural category as dbt Semantic Layer, Cube, and AtScale
- [[MCP]] — Mosaic exposes governed metrics to external AI agents (ChatGPT, Claude, Copilot, Gemini) via its own MCP server, the same pattern as Sigma's and Genie One's MCP servers
- [[Sigma]] — another vendor selling a warehouse-agnostic governed layer that other AI agents can call into, though Sigma stays closer to a live BI/spreadsheet surface where Mosaic positions itself as a pure semantic-layer product
- [[Market Landscape/TextQL|TextQL]] — another semantic-layer vendor emphasizing customer ownership of the underlying definitions (Git-backed Ontology vs. Mosaic's own governed store)
