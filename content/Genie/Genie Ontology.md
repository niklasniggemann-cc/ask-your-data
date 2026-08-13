---
title: Genie Ontology
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Enterprise Context Layer
tags:
  - genie
  - databricks
---

## Definition

Genie Ontology is Databricks' continuously-learned enterprise context layer, announced at DAIS 2026. It automatically extracts, maintains, and ranks a unified knowledge graph of business terms, metrics, and metadata across the organization — and feeds this context directly into Genie, enabling accurate responses without per-agent synonym curation.

Unlike [[Agent Metadata]] (manually curated, space-level synonyms) or [[Knowledge Store]] (space-level, per-agent), Genie Ontology operates at the organizational level and adapts continuously as terminology and data assets evolve.

## How It Works

Genie Ontology aggregates context from three sources:

1. **Unity Catalog semantic features** — Business Glossary, Domains, and [[Metric Views]] feed the ontology automatically
2. **External integrations** — 50+ connected applications (Slack, Jira, SharePoint, Confluence) surface terminology used across organizational silos
3. **Continuous learning** — query patterns and approved agent responses are folded back into the ontology over time

The **OntoRank Algorithm** — modeled on PageRank — ranks competing definitions by:
- Authority of the source (who defined it)
- Frequency of reference (how often it's used across the org)
- Proximity to certified assets in Unity Catalog
- Recency

This is Genie Ontology's answer to the [[Disambiguation]] problem: when "revenue" could mean five columns, OntoRank surfaces the most authoritative definition automatically — without requiring a human to manually curate synonyms.

## Performance Impact

In Databricks testing, Genie with Genie Ontology answered **84.5% of questions correctly on the first attempt**, versus 52.4% for the strongest general-purpose coding agent without the ontology layer. The improvement comes from reducing both [[Hallucinations]] and disambiguation failures.

## Unity Catalog Foundations

Genie Ontology builds on three Unity Catalog features:
- **Domains** (Public Preview) — business-aligned data organization
- **Glossary** (coming soon) — shared, governed business terminology
- **Pages** (Beta, Aug 2026) — governed, single-source definitions for business terms, acronyms, and KPIs; the human-modeled layer of the ontology that Genie One draws on directly to ground its answers

All three feed the ontology automatically when configured.

## Dynamic vs. Structural Disambiguation

| Approach | Mechanism | Trade-off |
|----------|-----------|-----------|
| Genie Ontology (dynamic) | OntoRank over usage + authority signals | Works without curation; less transparent |
| [[Agent Metadata]] (structural) | Explicit synonym mappings in UC | Deterministic; requires upfront curation |

Both are described in [[Disambiguation]]. They are complementary: Ontology reduces the need for manual curation; Agent Metadata handles cases where deterministic resolution is required.

## Availability

- **Genie One: Ontology snippets** — Public Preview (as of Aug 2026)
- Full ontology integration — GA with Genie, feeding Genie Agents and Genie One
- **Enabled by default** (Public Preview, Aug 6 2026) — previously opt-in; the ontology now applies automatically to Genie One conversations without admin configuration

## Recent Developments

- **2026-08-12** — **Pages** (Beta) added as a third Unity Catalog semantics foundation alongside Domains and Glossary — lets teams give business terms, acronyms, and KPIs a single governed definition that feeds directly into the ontology's human-modeled layer. [Source](https://docs.databricks.com/aws/en/uc-semantics/pages)
- **2026-08-06** — Genie Ontology is now **enabled by default** in Public Preview, removing the need for admins to turn it on manually before Genie One conversations get ontology-grounded context. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

## Related

- [[Disambiguation]] — the core problem Genie Ontology solves dynamically
- [[Unity Catalog]] — the governed foundation (Glossary, Domains, Metrics) that feeds the ontology
- [[Genie Agents]] — primary consumer; ontology grounding without per-agent configuration
- [[Genie One]] — unified interface that benefits from ontology-grounded responses
- [[Agent Metadata]] — structural complement: explicit synonym mappings at the space level
- [[Knowledge Store]] — space-level semantic store; Genie Ontology operates at the org level
- [[Hallucinations]] — the failure mode Genie Ontology reduces
- [[Fabric IQ]] — Microsoft's closest analogue: a context layer that grounds AI agents in governed business meaning, though built semantic-model-first rather than as a continuously-learned graph
