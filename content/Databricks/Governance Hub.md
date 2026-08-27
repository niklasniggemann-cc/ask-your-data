---
title: Governance Hub
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Data Governance
tags:
  - databricks
---

## Definition

Governance Hub is Databricks' account-level UI for monitoring governance across an entire Databricks estate — hundreds of workspaces and regions — from one place, rather than piecing metadata together from system tables, workspace-level views, and third-party tools. It sits above [[Unity Catalog]] and Unity AI Gateway, giving platform/governance teams and account admins a single unified view of data health, AI usage, and cost, with prioritized, agentic recommendations. Reached the account console **Previews** page in Beta on August 26, 2026 (docs confirm the underlying pages were already live by August 21).

## Core Pages

- **Data** — asset inventory, tagging/ownership/classification coverage, data quality and unhealthy/undocumented metastores; drill down to exactly which tables/schemas need attention
- **AI** — token consumption, model activity, per-user spend, and guardrail coverage across Unity AI Gateway traffic (Databricks-hosted and externally-hosted models, agents, tools, MCPs); budget-threshold alerts
- **Cost** — 30-day spend, month-to-date, daily average vs. prior period, tagged-vs-untagged spend, drill-down by product/workspace/resource/tag
- **Tags** (Beta, first shipped Aug 13, 2026) — centralized view of governed tag usage, recent assignments and their sources, recommendations to fix invalid values and tag important but untagged assets
- **Access Insights** — a single principal-centric view of what any user, group, or service principal can access across the account (direct grants, inherited group access, ownership), filterable by catalog or privilege

## Role in the AI Stack

Governance Hub is integrated with [[Genie Agents|Genie]]: instead of only pre-built views and static dashboards, admins can ask plain-language questions like "Why has there been a spike in costs" or "Show me tables with sensitive data that lack masking policies" and get answers grounded in the account's actual governance data — Genie understands the context of each vertical (Data, AI, Cost). Databricks' stated roadmap has Genie moving from answering questions to *taking actions* directly — configuring policies, setting up alerts, and implementing recommendations — making Governance Hub a case of natural-language interfaces reaching into the governance/admin layer itself, not just business data.

Respects existing Unity Catalog permissions; introduces no new access controls. Account admins get full access; workspace admins see Cost and AI for their workspaces; metastore admins see Data for their metastores.

## Recent Developments

- **2026-08-26** — **Governance Hub reaches Beta as a full account-level product** — public "Introducing Governance Hub" announcement bundling the Data, AI, and Cost pages (plus Access Insights) into one unified experience across AWS, Azure, and GCP, with Genie-powered agentic insights. Expands well beyond the previously-tracked Tags page alone. Enabled via the account console Previews page. [Source](https://www.databricks.com/blog/introducing-governance-hub-intelligent-account-level-governance-over-your-databricks-estate) / [Source](https://docs.databricks.com/aws/en/admin/governance-hub/)
- **2026-08-13** — **Tags page in Governance Hub** (Beta) — the first piece of Governance Hub tracked in this vault: a centralized account-wide view of governed tag usage. [Source](https://docs.databricks.com/aws/en/admin/governance-hub/tags)

## Related

- [[Unity Catalog]] — the governance layer Governance Hub provides an account-level view over
- [[Genie Agents]] — powers Governance Hub's natural-language Q&A over governance data
- [[Genie One]] — the broader Genie chat surface Governance Hub's agentic insights extend into the admin/governance domain
- [[Data Governance]] — the broader practice Governance Hub gives visibility into
