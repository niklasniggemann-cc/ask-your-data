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
- **SpotterModel** — builds semantic models without writing code (reached GA Aug 2026)
- **SpotterCode** — AI-assisted code generation for embedded analytics applications
- **Spotter Analysts** (Early Access, Aug 2026) — focused, governed sub-agents scoped to a specific team/domain: configure once which data models the agent can see, custom instructions, connectors, and workspace sharing, then open a pre-configured Spotter experience instead of the general one

## Market Position

ThoughtSpot was named a **Leader in the 2026 Gartner® Magic Quadrant™ for Analytics and Business Intelligence Platforms** (July 2026) — one of the only independent (non-hyperscaler-owned) vendors in the Leaders quadrant. Gartner specifically cited conversational analytics through Spotter, external semantic-layer connectivity, and agent workflow orchestration as differentiating strengths.

## Recent Developments

**2026-08-18** — ThoughtSpot Cloud 26.8.0.cl release: **SpotterModel reached GA** (auto-generates optimized semantic Models — table selection, joins, column selection — with review/customize at each step); **Spotter Analysts** entered Early Access (see Core Capabilities above); **Spotter starter prompts** let admins configure suggested first questions to guide new users; **Share chats** (Early Access) lets a user hand off a full Spotter conversation thread — questions, iterations, and analysis — rather than a screenshot; **SpotterViz insight tiles** (Early Access) add AI-generated text analysis tiles to a Liveboard that re-run against live data on every load. [Source](https://docs.thoughtspot.com/cloud/26.8.0.cl/notes)

## Related

- [[Genie Agents]] — Databricks' equivalent curated NL-to-SQL interface
- [[Genie One]] — Databricks' unified chat surface across agents; comparable in ambition to Spotter's role across the ThoughtSpot suite
- [[Snowflake CoWork]] — Snowflake's competing personal work agent, broader in scope (action-taking, not just Q&A)
- [[Looker Conversational Analytics]] — Google Cloud's competing conversational layer, hyperscaler-owned unlike Spotter
- [[Sigma]] — another independent, non-hyperscaler-owned conversational-BI vendor, warehouse-native rather than platform-bundled like Spotter
- [[Natural Language to SQL]] — the underlying technique both Spotter and Genie build on, and where it fails without governance
- [[Semantic Layer]] — the shared-meaning layer SpotQL and Unity Catalog-backed Genie both depend on
- [[Tableau Next]] — another independent-ish (Salesforce-owned) conversational-analytics platform, built on Salesforce Data Cloud/Agentforce rather than ThoughtSpot's own engine
