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
- **Ontologies** (rolling out after initial GA) — a further layer above semantic models for representing business concepts and relationships, extending Fabric IQ from "answer questions about this report" toward org-wide business context, similar in ambition to Genie Ontology's Domains/Glossary/Pages foundation
- **Fabric IQ plugin/skill for Microsoft 365 Copilot Cowork** (Preview) — lets a Cowork chat be grounded in a specific Power BI report, or reference one by name for Cowork's own search to resolve; answers stay consistent with what the same user sees in the actual report because Fabric IQ enforces the same permissions and semantic model
- Initial scope: Power BI reports and semantic models; Fabric data agents and ontologies are planned expansions

## Availability

- **Fabric IQ** — Generally Available as of June 2, 2026 (Build 2026 opening day)
- **Ontologies within Fabric IQ** — planned GA in the months following Build 2026, not yet confirmed live
- **Fabric IQ plugin in Copilot Cowork** — Preview, available to Power BI customers using Cowork
- Not previously tracked in this vault; this entry is a first-coverage backfill of a June 2026 milestone, not a same-day announcement

## Market Position

Extends Microsoft's "ask your data" story beyond the existing Copilot Chat → Power BI semantic model path (already tracked in [[Market Landscape/Updates|Market Landscape Updates]]) into a named, general-purpose context layer that other Microsoft 365 Copilot surfaces — not just Power BI itself — can ground answers in. Functionally the closest analogue in this vault is [[Genie Ontology]]: both aim to let an AI agent answer from governed business meaning rather than per-agent curation, though Fabric IQ starts from existing semantic models rather than a continuously-learned org-wide graph.

## Related

- [[Genie Ontology]] — Databricks' equivalent context/ontology layer that grounds Genie's answers
- [[Semantic Layer]] — the broader architectural pattern; Fabric IQ is built directly on Power BI's existing semantic models
- [[Snowflake CoWork]] — competing hyperscaler-adjacent personal work agent with its own context layer (Cortex Sense)
- [[Agent Metadata]] — Databricks' structural/deterministic complement to ontology-style grounding; a useful comparison point for how Fabric IQ's semantic-model-first approach differs
