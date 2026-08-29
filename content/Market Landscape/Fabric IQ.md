---
title: Fabric IQ
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Microsoft]]"
category: Enterprise Context Layer
tags:
  - market-landscape
  - semantic
---

## Definition

Fabric IQ is Microsoft's shared context/semantic layer for AI agents built on Microsoft Fabric — part of the broader "Microsoft IQ" family (alongside Work IQ, Foundry IQ, Web IQ) announced at Build 2026. It plays the same functional role for Microsoft's stack that [[Genie Ontology]] plays for Databricks and Cortex Sense plays for [[Snowflake CoWork]]: a governed, business-meaning layer that AI agents ground their answers in, rather than reasoning directly over raw tables.

## Core Capabilities

- **Semantic models as the grounding layer** — Fabric IQ builds on existing Power BI semantic models rather than requiring separate modeling; a well-structured semantic model becomes directly consumable as AI-agent context
- **Ontologies** (Preview, not yet GA) — a further layer above semantic models for representing business concepts and relationships, extending Fabric IQ from "answer questions about this report" toward org-wide business context, similar in ambition to Genie Ontology's Domains/Glossary/Pages foundation. As of Aug 2026, the Ontology item itself is queryable via a standards-based MCP server (see Recent Developments) — an agent-facing query interface exists even though the underlying Ontology item is still Preview.
- **Fabric IQ plugin/skill for Microsoft 365 Copilot Cowork** (Preview) — lets a Cowork chat be grounded in a specific Power BI report, or reference one by name for Cowork's own search to resolve; answers stay consistent with what the same user sees in the actual report because Fabric IQ enforces the same permissions and semantic model
- Initial scope: Power BI reports and semantic models; Fabric data agents and ontologies are planned expansions

## Availability

- **Fabric IQ** — Generally Available as of June 2, 2026 (Build 2026 opening day)
- **Ontologies within Fabric IQ** — Preview (Ontology item exists and is queryable, including via MCP as of Aug 2026); not yet GA
- **Fabric IQ plugin in Copilot Cowork** — Preview, available to Power BI customers using Cowork
- Not previously tracked in this vault; this entry is a first-coverage backfill of a June 2026 milestone, not a same-day announcement

## Market Position

Extends Microsoft's "ask your data" story beyond the existing Copilot Chat → Power BI semantic model path (already tracked in [[Market Landscape/Updates|Market Landscape Updates]]) into a named, general-purpose context layer that other Microsoft 365 Copilot surfaces — not just Power BI itself — can ground answers in. Functionally the closest analogue in this vault is [[Genie Ontology]]: both aim to let an AI agent answer from governed business meaning rather than per-agent curation, though Fabric IQ starts from existing semantic models rather than a continuously-learned org-wide graph.

## Recent Developments

- **2026-08-29** (docs last updated Aug 4, 2026) — **Fabric IQ Ontology MCP reaches Preview.** The Fabric IQ Ontology (Preview, not GA) is now queryable via a standards-based MCP server — `list_ontology_entity_types` for schema exploration and `search_ontology` for natural-language question answering over the ontology (returns JSON, optionally with a derived NL answer) — connectable from Microsoft Copilot Studio (as an addable agent tool), VS Code Agent Mode, or any other MCP client. Requires Fabric F2+/Power BI Premium P1+ capacity with the Ontology (preview) item enabled. Extends Fabric IQ from "ground Copilot Cowork in one Power BI report" toward the same "expose the semantic/context layer over MCP for any agent" pattern as Databricks' Genie One MCP server and Snowflake's Cortex Agents/MCP-packaged Native Apps. [Source](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-fabric-iq-ontology)
- **2026-08-20** (effective Aug 26, 2026) — **Copilot in Power BI drops direct Fabric data agent integration.** Microsoft is retiring the ~1-year-old integration that let Copilot in Power BI query a Fabric data agent directly; after Aug 26, 2026, Copilot in Power BI can no longer connect to Fabric data agents this way (the Fabric data agent experience itself is unaffected). Microsoft's stated alternative paths: Microsoft 365 Copilot (the same consolidated "ask your data from anywhere" surface behind the Aug 11 Copilot Chat → Power BI semantic model integration already logged in [[Market Landscape/Updates|Market Landscape Updates]]), or Copilot Studio/Microsoft Foundry/MCP-based integrations for custom experiences. Reads as a consolidation move — collapsing a narrower, older Copilot-to-data-agent path in favor of the newer semantic-model-grounded, Fabric-IQ-adjacent Copilot experience. [Source](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/retirement-of-fabric-data-agent-integration-in-copilot-in-power-bi/5328344)

## Related

- [[Genie Ontology]] — Databricks' equivalent context/ontology layer that grounds Genie's answers
- [[Semantic Layer]] — the broader architectural pattern; Fabric IQ is built directly on Power BI's existing semantic models
- [[Snowflake CoWork]] — competing hyperscaler-adjacent personal work agent with its own context layer (Cortex Sense)
- [[Agent Metadata]] — Databricks' structural/deterministic complement to ontology-style grounding; a useful comparison point for how Fabric IQ's semantic-model-first approach differs
