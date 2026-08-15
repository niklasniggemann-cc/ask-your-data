---
title: Unity Catalog
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Data Governance
tags:
  - databricks
---

## Definition

Unity Catalog is Databricks' unified governance layer that provides centralized metadata management, access control, lineage tracking, and data discovery across all data assets in the platform. It is the governance foundation beneath [[Genie Agents]], [[Agent Metadata]], and the [[Semantic Layer]] in Databricks.

## Core Capabilities

- **Metadata management** — descriptions and comments at database, table, column, and commit levels
- **Fine-grained access control** — row-level security and column masking that travel with each asset
- **Data lineage** — tracks which source tables feed each asset and which downstream consumers depend on it
- **Data discovery** — searchable, auditable catalog across the entire data estate
- **[[Metric Views]]** — governed semantic objects that define measures and dimensions over source tables

## Role in the AI Stack

Every [[Genie Agents]] space is built on Unity Catalog-registered data — Genie uses the metadata attached to those objects. [[Agent Metadata]] is defined within Unity Catalog and automatically consumed by all downstream tools. Row filters and column masks defined in Unity Catalog are enforced per-user at query time inside Genie.

Unity AI Gateway (part of Unity Catalog, GA August 2026) provides a single oversight location for [[MCP]] connections, tool costs, and agent permissions. Its **Smart Routing** capability (Beta) dynamically routes each request to the model best suited to it — by quality, cost, performance, availability, and budget — reserving expensive frontier models for tasks that need them and routing simpler work to cheaper models automatically. As of August 6, 2026, all Databricks-managed MCP connectors for [[Genie One]] and [[Genie Code]] have also migrated under Unity AI Gateway, bringing them into the same centralized governance, access control, and visibility as other MCP servers and tools (users must reauthenticate affected connectors).

## Recent Developments

- **2026-08-13** — **Tags page in Governance Hub** (Beta) — a centralized account-wide view of governed tag usage: recent assignments and their sources, plus recommendations to fix invalid tag values and tag important but untagged assets. [Source](https://docs.databricks.com/aws/en/admin/governance-hub/tags)
- **2026-08-11** — **ABAC GRANT policies** extended beyond models to cover model services, model provider services, MCP services, agent services, and skills (Beta) — dynamic attribute-based access grants now reach the AI-agent surface itself, not just underlying data assets. [Source](https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/grant-policies)
- **2026-08-07** — **Tag automations** (Beta) auto-assign or remove governed tags on matching tables/volumes; rules can be authored by describing them to [[Genie Agents|Genie]] in natural language instead of only via a form. [Source](https://docs.databricks.com/aws/en/admin/governed-tags/automate-tag-assignment)

## Related

- [[Databricks]] — platform that owns Unity Catalog
- [[Agent Metadata]] — YAML-defined business context governed within Unity Catalog
- [[Metric Views]] — semantic objects defined in Unity Catalog
- [[Genie Agents]] — primary AI consumer of Unity Catalog metadata and permissions
- [[Data Lineage]] — lineage tracking as a Unity Catalog capability
- [[Data Governance]] — the broader practice Unity Catalog implements structurally
- [[OntoBricks]] — open-source project that materializes Unity Catalog tables into a reasoned knowledge graph
