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
- **Microsoft 365 extensions** (GA, Aug 2026) — Excel, PowerPoint, Word, and Outlook add-ins that let Quick act (not just answer) directly inside those apps

## Status and History

Announced October 9, 2025 as an evolution of QuickSight, rolled out globally starting that day; new agentic capabilities launched first in US East (N. Virginia), US West (Oregon), Europe (Dublin), and Asia Pacific (Sydney), with other regions retaining QuickSight functionality under the new branding. Existing compliance certifications (SOC, HIPAA, ISO, GDPR, FedRAMP) carried over unchanged. Since informally referred to as "Amazon Quick" in 2026 branding.

## Recent Developments

**2026-09-01** — **Apps in Quick reaches GA**: build full custom applications (project trackers, customer dashboards, training portals, internal tools) from a natural-language description, for Plus/Professional/Enterprise customers. Apps connect live to existing business systems (Salesforce, Jira, Asana, ServiceNow, M365, Google Workspace, databases/warehouses), inherit existing identity/access-control policies, stay current as data changes, and can be published/shared; further edits are made by describing them. Amazon's entry into the same "NL-authored internal app" space as [[Market Landscape/TextQL|TextQL]] Data Apps and Sigma Workbooks-as-Code. [Source](https://aws.amazon.com/about-aws/whats-new/2026/09/amazon-quick-custom-apps-natural-language/)

**2026-08-31** (backfilled, effective 2026-07-31) — **Amazon Q Business closed to new customers**: AWS will keep providing bug fixes/security updates to existing Q Business customers but no longer accepts new customers or feature requests, and now directs anyone wanting similar or more advanced generative-BI/agentic capabilities to Amazon Quick. Published migration guide covers a Bring-Your-Own-Index path (attach an existing Q Business index to Quick as a knowledge base without disrupting the live app), manual Q Apps → Quick Flows conversion, and gaps around guardrails, granular ACLs outside IAM Identity Center, and MCP-based connectors for sources without a native Quick integration. Confirms Quick as AWS's single forward-going NL work-agent platform rather than one of two overlapping products. [Source](https://docs.aws.amazon.com/amazonq/latest/qbusiness-ug/qbusiness-availability-change.html)

**2026-08-17** — **Microsoft 365 extensions reach GA**: add-ins for Excel, PowerPoint, Word, and Outlook let Quick act directly inside those apps — Excel spreadsheet analysis/pivot tables/charts, PowerPoint deck generation from Quick data against org templates, Word tracked-change editing and comment review, Outlook inbox triage/organization and reply drafting using Quick data plus inbox context. Live in six regions (US East/West, Sydney, Dublin, Tokyo, Frankfurt). Goes beyond NL query answering into task execution inside the apps users already work in. [Source](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-quick-microsoft-365-extensions-generally-available/)

**2026-08-06** — **Multi-dataset topics** reached GA: a "topic" (Quick's semantic-model construct) can now span multiple datasets with relationships defined once, and Quick performs the joins at runtime — for both dashboard-building (a single visual can pull fields from multiple datasets without manual pre-joining) and natural-language Q&A (the chat agent reads the topic's relationships and joins across datasets to answer). Previously, cross-dataset questions required pre-joining data into a single dataset first, burning extra SPICE capacity and duplicating models per use case. Existing dataset-level RLS/CLS permissions carry through. [Source](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-quick/)

**2026-08-11** — Amazon Quick's agentic AI capabilities (including natural-language chat) became available in AWS GovCloud (US-West) (FedRAMP Class D), letting government/regulated customers build mission-specific chat agents (procurement, compliance, grants) with data processed entirely within GovCloud. Minor, regional-availability item. [Source](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-quick-aws-govcloud-us-west/)

## Related

- [[Genie One]] — Databricks' closest equivalent: a unified natural-language surface across an organization's governed data and tools
- [[Snowflake CoWork]] — Snowflake's comparable evolution from a narrower conversational-analytics layer (Snowflake Intelligence) into a broader personal work agent
- [[Sigma]] — also ships governed dashboard-migration tooling (Workbooks as Code) as part of its own BI-migration play
- [[Tableau Next]] — another platform vendor's expansion of a BI product into a broader NL work-agent suite
