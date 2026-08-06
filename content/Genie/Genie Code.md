---
title: Genie Code
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: AI Coding Assistant
tags:
  - genie
  - databricks
---

## Definition

Genie Code is [[Databricks]]' AI coding assistant for developers and data practitioners, deeply integrated into the workspace. It is context-aware via [[Unity Catalog]] — understanding tables, columns, and lineage — and adapts its capabilities based on the current product surface.

## Surface-Specific Capabilities

| Surface | Genie Code focus |
|---------|-----------------|
| Lakeflow Pipelines Editor | Pipeline editing and data engineering |
| Notebooks / SQL Editor | Data exploration and analysis |
| Dashboards | Data analysis and dashboard creation |

## Core Capabilities

- Inline suggestions and quick fixes
- Error diagnosis
- Sample data exploration
- Multi-step agentic tasks — handles complex requests autonomously
- Creates [[Genie Agents]] from a natural-language description
- Personalizable via [[Agent Skills]], instructions, and MCP servers (Full page Genie Code, GA August 2026)

## Unity Catalog Integration

Genie Code reads table and column metadata, descriptions, and lineage from [[Unity Catalog]], so suggestions are grounded in the actual data structure rather than generic patterns.

## Related

- [[Genie One]] — unified chat that Genie Code operates alongside
- [[Genie Agents]] — agents that Genie Code can create and review
- [[Unity Catalog]] — source of schema and lineage context
- [[Agent Skills]] — the mechanism Genie Code uses for personalization
- [[Databricks]] — platform
