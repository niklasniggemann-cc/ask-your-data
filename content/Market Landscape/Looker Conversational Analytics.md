---
title: Looker Conversational Analytics
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Google Cloud]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

Conversational Analytics is Google Cloud's natural-language query layer for Looker and BigQuery, exposed to developers as the **Conversational Analytics API** (formerly the Data QnA API) and to end users through Gemini-powered chat inside Looker, BigQuery, and Gemini Enterprise. It lets business users ask plain-English questions and get back grounded answers, SQL/LookML queries, and visualizations — Google's direct answer to the same problem [[Genie Agents]], [[ThoughtSpot Spotter]], and [[Snowflake CoWork]] solve on their respective platforms.

## Core Capabilities

- **Data agents** — persistent, configurable AI agents scoped to a Looker Explore, BigQuery dataset, or (in Preview) AlloyDB/Cloud SQL/Spanner source, each with authored context (glossary terms, example query pairs, synonyms, golden queries)
- **Reasoning transparency** — response streams include `THOUGHT` messages showing step-by-step reasoning and `PROGRESS` messages during data-value search, not just a final answer
- **Agent-to-agent (A2A) protocol support** (Preview, GA'd June 2026) — lets a Looker/BigQuery data agent be orchestrated by or coordinate with other agents rather than only serving a chat UI directly
- **Gemini Enterprise publishing** — a Conversational Analytics data agent built in Looker can be published directly into Gemini Enterprise, carrying governed answers into a broader agent workflow surface outside Looker itself
- Enterprise controls: CMEK, VPC Service Controls, Cloud Audit Logs, data residency via regional/multi-regional endpoints

## Availability

- **Conversational Analytics API** — GA for BigQuery and Looker as of June 23, 2026; still Preview for AlloyDB, Cloud SQL for MySQL/PostgreSQL, and Spanner sources
- Not previously tracked in this vault; this entry is a first-coverage backfill, not a same-day announcement

## Recent Developments

- **2026-08-04** (Preview, part of the Looker 26.12 rollout) — a **Responses & Feedback** tab on the Conversational Analytics System Activity dashboard lets admins review end-user query success rates, rating distributions, and written feedback, gated behind an opt-in admin setting and per-user consent to share query data. [Source](https://docs.cloud.google.com/looker/docs/release-notes)
- **2026-08-03 to 08-07** (Looker 26.12 rollout) — Conversational Analytics data agents published to Gemini Enterprise now render charts and visualizations inline in agent responses (previously text/table only); query timeout increased from 2 to 5 minutes; data agent editors can toggle whether the agent shows its thinking/debugging steps in responses. [Source](https://cloud.google.com/blog/products/business-intelligence/looker-updates-for-agentic-bi-at-next26)
- **2026-06-23** — Conversational Analytics API reached GA for BigQuery and Looker, alongside A2A protocol support (Preview) and enterprise security/compliance features (CMEK, VPC-SC, data residency). [Source](https://docs.cloud.google.com/gemini/data-agents/conversational-analytics-api/release-notes)

## Related

- [[Genie Agents]] — Databricks' equivalent curated NL-to-SQL interface
- [[Genie One]] — Databricks' unified chat surface; comparable in ambition to Gemini Enterprise's role for published data agents
- [[ThoughtSpot Spotter]] — independent-vendor competitor in the same category
- [[Snowflake CoWork]] — hyperscaler-adjacent competitor with broader action-taking scope
- [[Semantic Layer]] — LookML is one of the original semantics-as-code implementations this product now layers conversational AI on top of
- [[Natural Language to SQL]] — the underlying technique the Conversational Analytics API implements
