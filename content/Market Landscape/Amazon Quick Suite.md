---
title: Amazon Quick Suite
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Amazon]]"
category: Natural Language Data Interface
tags:
  - market-landscape
  - conversational-bi
---

## Definition

Amazon Quick Suite (informally shortened to "Amazon Quick" in 2026) is AWS's rebrand and expansion of **Amazon QuickSight** into a broader natural-language work-agent platform. QuickSight's existing BI functionality — dashboards, datasets, analyses, embedding — continues unchanged under a **Quick Sight** section, now surrounded by a set of AI-powered agents reachable through a single natural-language interface, **Quick chat**.

## Core Capabilities

- **Quick Sight** — the original QuickSight BI surface (dashboards, datasets, analyses, Stories), functionally unchanged by the rebrand
- **Quick chat** — the natural-language entry point for the whole suite, prominently featured on the home page
- **Quick Research** — delivers cited insights synthesized from enterprise and public data sources
- **Quick Flows** — creates and shares workflow automations from natural-language descriptions (e.g. turning meeting notes into action items, automating recurring reports)
- **Quick Automate** — handles complex, multi-step business processes
- **Quick Index** — a shared knowledge base spanning company documents and data
- **Quick spaces** — lets teams customize which capabilities and data sources are available to them
- **BI migration agents** (via AWS Transform) — convert Power BI and Tableau dashboards into Quick Sight assets automatically, reducing migration effort from months to days

## Status and History

Announced October 9, 2025 as an evolution of QuickSight, rolled out globally starting that day; new agentic capabilities launched first in US East (N. Virginia), US West (Oregon), Europe (Dublin), and Asia Pacific (Sydney), with other regions retaining QuickSight functionality under the new branding. Existing compliance certifications (SOC, HIPAA, ISO, GDPR, FedRAMP) carried over unchanged. Since informally referred to as "Amazon Quick" in 2026 branding.

## Recent Developments

**2026-08-06** — **Multi-dataset topics** reached GA: a "topic" (Quick's semantic-model construct) can now span multiple datasets with relationships defined once, and Quick performs the joins at runtime — for both dashboard-building (a single visual can pull fields from multiple datasets without manual pre-joining) and natural-language Q&A (the chat agent reads the topic's relationships and joins across datasets to answer). Previously, cross-dataset questions required pre-joining data into a single dataset first, burning extra SPICE capacity and duplicating models per use case. Existing dataset-level RLS/CLS permissions carry through. [Source](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-quick/)

**2026-08-11** — Amazon Quick's agentic AI capabilities (including natural-language chat) became available in AWS GovCloud (US-West) (FedRAMP Class D), letting government/regulated customers build mission-specific chat agents (procurement, compliance, grants) with data processed entirely within GovCloud. Minor, regional-availability item. [Source](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-quick-aws-govcloud-us-west/)

## Related

- [[Genie One]] — Databricks' closest equivalent: a unified natural-language surface across an organization's governed data and tools
- [[Snowflake CoWork]] — Snowflake's comparable evolution from a narrower conversational-analytics layer (Snowflake Intelligence) into a broader personal work agent
- [[Sigma]] — also ships governed dashboard-migration tooling (Workbooks as Code) as part of its own BI-migration play
