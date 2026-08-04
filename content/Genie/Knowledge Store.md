---
title: Knowledge Store
type: "[[Concept]]"
vendor: "[[Databricks]]"
scope: Genie Agent (space-level)
tags:
  - genie
  - databricks
---

## Definition

The Knowledge Store is a space-level collection of curated semantic definitions that extends [[Unity Catalog]] metadata within a specific [[Genie Agents]] space. It lets space authors customize and enrich business context without altering the underlying Unity Catalog objects.

Every Genie space has its own Knowledge Store — definitions are scoped to that space.

## What It Contains

- **Table and column descriptions** — customized for the space's context, separate from Unity Catalog metadata
- **Business terms and synonyms** — maps the language users naturally speak to columns and measures
- **Hidden columns** — marks irrelevant or sensitive columns invisible within this space
- **SQL expressions** — structured definitions for KPIs, business attributes, and conditions
- **Join relationships** — pre-defined joins between tables so Genie doesn't guess
- **Example SQL queries** — static or parameterised queries that teach Genie how to answer common questions

## How Genie Learns from It

Genie uses the Knowledge Store in two ways:
1. **Direct matching** — uses an example SQL query verbatim when a user prompt closely matches
2. **Pattern learning** — infers from examples how to handle similar but novel questions

Genie also learns from interaction: when authors approve responses or download results, Genie suggests new SQL expressions or join relationships that could improve future accuracy.

## Relationship to Unity Catalog

The Knowledge Store does not replace [[Unity Catalog]] metadata — it extends it within a specific space. Unity Catalog provides the foundation (table descriptions, column comments, governance); the Knowledge Store adds space-specific business language and logic on top.

## Trusted Responses

Responses generated from parameterised example queries or Unity Catalog SQL functions are marked **Trusted** — a signal to users that results follow established organizational logic rather than Genie's best interpretation.

## Related

- [[Genie Agents]] — the product that owns and uses the Knowledge Store
- [[Unity Catalog]] — the metadata and governance foundation beneath it
- [[Data Quality]] — quality practices that feed into what the Knowledge Store encodes
- [[Semantic Layer]] — the broader architectural principle the Knowledge Store implements at the space level
- [[Agent Metadata]] — the Unity Catalog-level complement (governed globally vs. space-locally)
