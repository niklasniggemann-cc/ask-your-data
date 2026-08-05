---
title: Disambiguation
type: "[[Concept]]"
context: AI, Semantic Layer, Data Tools
tags:
  - semantic
---

## Definition

Disambiguation is the process of resolving an ambiguous user query term to a specific, authoritative data definition when multiple candidates exist. It is a core challenge in natural language data interfaces: the same word can plausibly map to different columns, metrics, or concepts depending on team, context, or phrasing.

## Why It's Hard

As schemas scale and terminology diverges across departments:
- "Revenue" could mean MRR, NRR, GRR, ARR, or expansion revenue
- "Net retention" means one thing to Finance and something different to Product
- A model inferring from column names cannot know which definition is authoritative

Pattern recognition alone fails not because of a model limitation, but because **ambiguity, scale, and terminological inconsistency exceed what inference can resolve**.

## Approaches

### Structural Disambiguation (Agent Metadata)

[[Agent Metadata]] resolves disambiguation explicitly: synonyms map user terms to specific columns deterministically. No inference required. The mapping is governed in [[Unity Catalog]], version-controlled, and consumed automatically by all downstream tools.

Advantage: deterministic, auditable, consistent across all users and tools.
Limitation: requires upfront curation; someone must define the mappings.

### Dynamic Disambiguation (Genie Ontology)

[[Genie Ontology]] resolves disambiguation at runtime using a PageRank-like ranking (OntoRank) over a graph of all organizational data assets. When multiple definitions exist for the same term, it ranks them by:
- Authority of the source (who defined it)
- Frequency of reference (how often it's used)
- Proximity to certified assets
- Recency

Advantage: works without manual curation; adapts as the organization evolves.
Limitation: less transparent than explicit mappings; relies on usage patterns being meaningful.

## Related

- [[Agent Metadata]] — structural disambiguation via synonyms in Unity Catalog
- [[Genie Ontology]] — dynamic disambiguation via OntoRank over organizational data assets
- [[Semantic Layer]] — the architectural layer that makes disambiguation deterministic
- [[Natural Language to SQL]] — where disambiguation failures manifest as wrong queries
- [[Knowledge Store]] — space-level disambiguation layer for Genie Agents
