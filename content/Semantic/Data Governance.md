---
title: Data Governance
type: "[[Concept]]"
context: Data Engineering, Platform Engineering
tags:
  - semantic
  - databricks
---

## Definition

Data governance is the set of policies, processes, and standards that ensure data is used correctly, consistently, and securely across an organization. In a well-designed data platform, governance is **structural** — enforced by construction, traveling with the data asset — rather than **procedural** — documented separately and relying on people to follow the rules.

## The Structural vs. Procedural Distinction

| Procedural governance | Structural governance |
|----------------------|----------------------|
| Policy documents | Access controls in the data platform |
| Manual approval workflows | Row/column security enforced at query time |
| Wiki pages with metric definitions | [[Metric Views]] in [[Unity Catalog]] |
| Tribal knowledge about join logic | [[Agent Metadata]] synonyms in the catalog |

The [[Semantic Layer]] argument is fundamentally a governance argument: when business semantics live inside the data platform, every tool reads from the same governed truth by construction.

## Governance in AI Systems

AI tools amplify governance failures — an LLM wraps poorly governed data in confident-sounding prose. Good governance upstream is the precondition for trustworthy AI output downstream. Three layers matter most:

1. **Data quality governance** — [[Medallion Architecture]] ensures clean data reaches the AI layer
2. **Metadata governance** — [[Unity Catalog]] and [[Agent Metadata]] ensure AI tools interpret data correctly
3. **Access governance** — Unity Catalog row/column security, enforced per user at query time in [[Genie Agents]]

## Related

- [[Unity Catalog]] — structural governance implementation in Databricks
- [[Governance Hub]] — account-level UI giving visibility into governance across a Databricks estate
- [[Semantic Layer]] — the broader architecture where governance becomes infrastructure
- [[Agent Metadata]] — metadata governance for AI consumption
- [[Data Quality]] — the data quality dimension of governance
- [[Data Lineage]] — provenance tracking as a governance component
