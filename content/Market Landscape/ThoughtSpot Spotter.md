---
title: ThoughtSpot Spotter
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[ThoughtSpot]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

Spotter is ThoughtSpot's conversational analytics agent — a natural-language interface over governed data that lets business users ask questions, explore follow-ups, and get answers with citations back to the underlying data. It is ThoughtSpot's direct answer to the same problem [[Genie Agents]] and [[Genie One]] solve on Databricks: making structured (and increasingly unstructured) enterprise data queryable in plain English without writing SQL.

## Core Capabilities

- Conversational Q&A over governed, semantically-modeled data, with follow-up exploration in the same thread
- **SpotQL** — a semantic query engine underneath Spotter built specifically to handle nested logic, comparative rankings, derived metrics, and multi-step filtering, rather than only single-shot lookups
- External semantic-layer connectivity — Spotter can reach into semantic layers outside ThoughtSpot itself rather than requiring all modeling to live natively in the platform
- Agent workflow orchestration across the surrounding agent suite (below)

## The Spotter Agent Family

ThoughtSpot has expanded Spotter from a single chat agent into a suite of purpose-built agents covering the analytics workflow end to end:
- **Spotter 3** — the core conversational agent; extended to bridge structured databases with unstructured sources (Slack, SharePoint), aiming at data that traditional BI tools can't reach
- **SpotterViz** — builds dashboards from natural language
- **SpotterModel** — builds semantic models without writing code
- **SpotterCode** — AI-assisted code generation for embedded analytics applications

## Market Position

ThoughtSpot was named a **Leader in the 2026 Gartner® Magic Quadrant™ for Analytics and Business Intelligence Platforms** (July 2026) — one of the only independent (non-hyperscaler-owned) vendors in the Leaders quadrant. Gartner specifically cited conversational analytics through Spotter, external semantic-layer connectivity, and agent workflow orchestration as differentiating strengths.

## Related

- [[Genie Agents]] — Databricks' equivalent curated NL-to-SQL interface
- [[Genie One]] — Databricks' unified chat surface across agents; comparable in ambition to Spotter's role across the ThoughtSpot suite
- [[Snowflake CoWork]] — Snowflake's competing personal work agent, broader in scope (action-taking, not just Q&A)
- [[Looker Conversational Analytics]] — Google Cloud's competing conversational layer, hyperscaler-owned unlike Spotter
- [[Sigma]] — another independent, non-hyperscaler-owned conversational-BI vendor, warehouse-native rather than platform-bundled like Spotter
- [[Natural Language to SQL]] — the underlying technique both Spotter and Genie build on, and where it fails without governance
- [[Semantic Layer]] — the shared-meaning layer SpotQL and Unity Catalog-backed Genie both depend on
