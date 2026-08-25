---
title: Semantic Layer
type:
  - "[[Concept]]"
  - "[[Architecture]]"
context: Data Architecture, AI Analytics
tags:
  - semantic
---

## Definition

The semantic layer is the architectural component that sits between source data and consuming systems — dashboards, notebooks, BI tools, AI agents — and translates physical data structures into a shared business vocabulary. It defines the metrics, dimensions, and sanctioned definitions that enable consistent data access across every downstream surface.

When strong: the entire organization moves faster and more reliably.
When weak or fragmented: different teams get different numbers for the same metric, an LLM answers instantly but contradicts the finance report, and a new hire spends their first week figuring out which dashboard to trust.


## Three Core Advantages

1. **Single source of truth** — metric definitions live in one place; every BI tool, notebook, and natural language interface returns the same answer
2. **Accelerated data access** — business users gain self-service analytics without needing to know the schema
3. **Structural governance** — row-level security, column masking, and certification policies travel with each metric definition rather than being re-implemented per tool

## Components

| Component | Role |
|-----------|------|
| Measures | Core calculations (revenue, churn rate, MAU) |
| Joins & relationships | Pre-defined paths between tables |
| Filters | Reusable filter logic |
| Metadata | Descriptions, tags, synonyms |
| Data lineage | Source tables → metric → downstream consumers |
| Access controls | Row/column security traveling with each asset |

## Historical Evolution

| Era | Development |
|-----|-------------|
| 1990s | MicroStrategy — first commercial semantic layers |
| Late 1990s | OLAP cubes — pre-aggregated, rigid, fast |
| 2000s | Enterprise BI — IT-managed centralized models |
| 2012 | LookML — semantics-as-code, version control |
| Now | Universal semantic layer — define once, serve via open APIs |

## Platform vs. Tool

**Traditional approach**: business logic embedded inside individual BI tools — governance is reinvented in every product and the correct answer depends on which tool you ask.

**Platform approach**: semantics managed inside the data platform, exposed to all surfaces via open APIs. Governance becomes enforced by construction. The semantic model is infrastructure every team and tool depends on.

## The Semantic Layer and AI

LLMs have no inherent understanding of a company's business vocabulary. Without a semantic layer they generate plausible queries that may be subtly or significantly wrong, presented with full confidence.

Two interaction modes for AI agents:

**Grounding** — before generating any query, the agent reads the semantic layer's descriptive context: available metrics, dimensions, definitions, and governance rules. Prevents hallucinated column names, incorrect joins, and misapplied filters.

**Execution** — the agent queries the semantic layer's interface using vetted metric definitions rather than raw tables. Output is auditable, consistent, and automatically filtered by security policies.

## Semantic Layer vs. Pure [[Natural Language to SQL]]

| | Pure Text-to-SQL | With Semantic Layer |
|--|-----------------|---------------------|
| Queries against | Raw tables | Governed metric definitions |
| Business logic | Inferred by LLM | Defined once, enforced structurally |
| Consistency | Varies by session | Same answer every time |
| Auditability | None | Full — traceable to metric definition |
| Governance | Re-implemented per query | Travels with the asset |

## GenAI Metadata

Beyond metric definitions, GenAI applications need:
- Natural language synonyms, display rules, example queries
- Domain-specific instructions that scope interpretation
- A continuous learning loop: query patterns → new concept proposals → structured additions

## Best Practices

1. Author once, reuse everywhere
2. Keep governance proximate to the asset
3. Design for openness — consumable by today's and tomorrow's tools
4. One source for humans and AI
5. Semantics as code — versioned, reviewed, tested
6. Start narrow: one high-stakes decision, one metric, then expand by usage

## Recent Developments

**2026-01-27** — Open Semantic Interchange (OSI) v1.0 released under Apache 2.0: a cross-vendor YAML spec for metrics, dimensions, and relationships, backed by Snowflake, dbt Labs, Cube, AtScale, Salesforce, Tableau, and 40+ others — aimed at one portable semantic definition instead of redefining business logic per BI tool. [Source](https://open-semantic-interchange.org/updates/)

**2026-02-03** — Snowflake's Semantic View Autopilot reached GA, auto-maintaining metric definitions and propagating them across dbt, Looker, Sigma, and ThoughtSpot via OSI connections. [Source](https://www.constellationr.com/insights/news/snowflake-cortex-code-semantic-view-autopilot-ga)

**2026-04-07** — dbt's rerun of its semantic-layer-vs-text-to-SQL benchmark on current-gen models: text-to-SQL accuracy nearly doubled since 2023 (32.7% → 64.5%), but the dbt Semantic Layer still hits ~98–100% on covered queries because it fails loudly (an error) rather than returning a plausible-but-wrong number. [Source](https://docs.getdbt.com/blog/semantic-layer-vs-text-to-sql-2026)

**2026-06-01** — Fivetran and dbt Labs completed their merger (all-stock, first announced Oct 2025), operating as "Fivetran + dbt Labs" with Fivetran's George Fraser as CEO and dbt's Tristan Handy as President; both products keep their names with no disruptive changes. The substantive product news: **Agents Schema**, a new open-source standard for agentic context — it designates a single schema in a warehouse or lake as the shared context layer for AI agents, storing metric definitions, semantic models, dbt lineage, and business documentation as plain SQL tables, publishable via GitHub Actions or metadata connectors, and readable by any SQL-capable agent regardless of vendor. Positioned as a customer-owned alternative to vendor-locked agent context systems — a second entrant alongside Open Semantic Interchange (above) in the push toward portable, non-proprietary semantic metadata for AI. Also shipped: dbt Core v2.0 (alpha, open-sourcing the Fusion engine runtime under Apache 2.0), dbt State (preview, incremental-build caching), and dbt Wizard (beta, an autonomous assistant for model authoring/refactoring grounded in lineage, tests, and defined metrics). [Source](https://www.fivetran.com/press/fivetran-dbt-labs-complete-merger-to-create-the-data-infrastructure-for-trusted-ai-agents) / [Source](https://www.techtarget.com/data-technologies/news/366643590/Fivetran-DBT-Labs-complete-merger-to-form-data-layer-for-AI)

## Related

- [[Data Governance]] — structural governance as a core benefit
- [[Data Lineage]] — provenance tracking within the semantic layer
- [[Natural Language to SQL]] — the alternative approach that lacks governance guarantees
- [[Genie Agents]] — a downstream consumer of the semantic layer via Unity Catalog
- [[ThoughtSpot Spotter]] — competing conversational-BI agent citing external semantic-layer connectivity as a differentiator
- [[OntoBricks]] — an open-source, standards-based (OWL/RDF) take on the same problem, built on Unity Catalog
- [[Looker Conversational Analytics]] — Google Cloud's conversational layer built on LookML, one of the original semantics-as-code implementations
- [[Fabric IQ]] — Microsoft's AI-agent context layer, built directly on Power BI semantic models
- [[Sigma]] — warehouse-native BI vendor whose agents ground themselves in governed Data Models, the same pattern as every other vendor here
- [[Snowflake CoWork]] — CoWork's data-answering layer (Cortex Agents → Cortex Analyst) depends on Snowflake's own semantic-layer stack for grounded answers; not to be confused with CoCo, Snowflake's separate coding-agent product
- [[Tableau Next]] — Salesforce's Tableau Semantics layer implements the same pattern, with plain-language model authoring and Salesforce as an OSI backer
- [[Market Landscape/TextQL|TextQL]] — an AI-analyst startup whose Ontology is a self-maintaining semantic layer stored as a customer-owned, Git-native file tree rather than a proprietary in-platform model
