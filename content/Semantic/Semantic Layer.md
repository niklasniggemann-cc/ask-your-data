---
title: Semantic Layer
type:
  - "[[Concept]]"
  - "[[Architecture]]"
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

## Related

- [[Data Governance]] — structural governance as a core benefit
- [[Data Lineage]] — provenance tracking within the semantic layer
- [[Natural Language to SQL]] — the alternative approach that lacks governance guarantees
- [[Genie Agents]] — a downstream consumer of the semantic layer via Unity Catalog
