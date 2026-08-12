---
title: Snowflake CoWork
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Snowflake]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

Snowflake CoWork is Snowflake's personal AI work agent for knowledge workers — a full rebrand and expansion of the earlier "Snowflake Intelligence" product, announced June 2, 2026 at Snowflake Summit 26. Where the Cortex Analyst / Snowflake Intelligence framing centered on "ask a question about governed data, get an answer," CoWork repositions the product around *taking action*: it reasons across multi-step tasks, automates routine work, and carries a business question through to a decision and an executed action, not just a chat answer.

## Core Capabilities

- **CoCo + CoWork** — CoCo answers questions over governed Snowflake data (the Cortex Analyst-style NL-to-SQL layer); CoWork sits above it and acts — running multi-step Deep Research reports, publishing interactive governed dashboards ("Artifacts"), and taking actions across external tools like Gmail, Slack, and Salesforce in natural language
- **Cortex Sense** — a context-enrichment layer Snowflake says lifts accuracy on complex enterprise queries from 47% to 83% when paired with CoCo/CoWork
- **Domain Agents** — pre-scoped agents for specific business domains, generally available alongside the core chat interface at ai.snowflake.com
- Personalization features layered on top of the existing Cortex Analyst / Cortex Agents / Cortex Search stack

## Market Position

Positions Snowflake's "ask your data" surface as a general-purpose agentic work assistant rather than a narrower BI chat feature, putting it in more direct competition with Microsoft Copilot (which spans Power BI and the rest of M365) than with narrower conversational-BI tools like [[ThoughtSpot Spotter]]. The rebrand had already happened by June 2026 but had not been captured in this vault's dedicated Snowflake coverage until this entry.

## Related

- [[Genie One]] — Databricks' equivalent unified chat surface across agents and external sources; similar ambition to unify "ask" and "act"
- [[ThoughtSpot Spotter]] — a narrower conversational-analytics agent by comparison, without CoWork's action-taking scope
- [[Natural Language to SQL]] — the underlying technique CoCo's data-answering layer builds on
- [[Semantic Layer]] — the governed-meaning layer CoCo depends on for grounded answers
