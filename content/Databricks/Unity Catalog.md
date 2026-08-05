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

Unity AI Gateway (part of Unity Catalog) provides a single oversight location for [[MCP]] connections, tool costs, and agent permissions.

## Related

- [[Databricks]] — platform that owns Unity Catalog
- [[Agent Metadata]] — YAML-defined business context governed within Unity Catalog
- [[Metric Views]] — semantic objects defined in Unity Catalog
- [[Genie Agents]] — primary AI consumer of Unity Catalog metadata and permissions
- [[Data Lineage]] — lineage tracking as a Unity Catalog capability
- [[Data Governance]] — the broader practice Unity Catalog implements structurally
- [[OntoBricks]] — open-source project that materializes Unity Catalog tables into a reasoned knowledge graph
