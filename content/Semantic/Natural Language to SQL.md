---
title: Natural Language to SQL
aliases:
  - Text-to-SQL
  - NL-to-SQL
type: "[[Concept]]"
tags:
  - semantic
---

## Definition

Natural Language to SQL (NL-to-SQL or Text-to-SQL) is the capability of converting a user's question expressed in plain language into a SQL query that can be executed against a database. It is the core mechanism behind conversational data analytics tools like [[Genie Agents]].

## How It Works

1. User submits a natural language question
2. The system maps question terms to available tables and columns
3. An LLM generates a SQL query from the mapped context
4. The query executes and results are returned

## The Governance Problem

Pure text-to-SQL — where the LLM queries raw tables directly — has a fundamental limitation in production:

- Business logic must be **inferred** from table names and column descriptions
- Results are **inconsistent** across sessions and model versions
- Generated queries are **unauditable** — no way to verify they reflect organizational metric definitions
- Governance is **absent** — no row-level security, column masking, or canonical definitions

A [[Semantic Layer]] solves this: the LLM queries governed metric definitions, not raw tables. The query becomes auditable, consistent, and backed by the same governance infrastructure as every other consumer.

## Inference vs. Definition

| | Pure Text-to-SQL | With Semantic Layer |
|--|-----------------|---------------------|
| Queries against | Raw tables | Governed [[Metric Views]] |
| Business logic | Inferred by LLM | Defined once, enforced structurally |
| Consistency | Varies by session | Same answer every time |
| Auditability | None | Traceable to metric definition |

## Disambiguation Challenge

When multiple columns are plausible matches for a query term, pure NL-to-SQL has no basis for choosing correctly. See [[Disambiguation]] for structural and dynamic solutions.

## Related

- [[Semantic Layer]] — the governance layer that makes NL-to-SQL trustworthy
- [[Genie Agents]] — Databricks implementation of governed NL-to-SQL
- [[Agent Metadata]] — provides synonyms that make term resolution deterministic
- [[Disambiguation]] — the core challenge NL-to-SQL faces at scale
- [[Hallucinations]] — the failure mode when NL-to-SQL gets it wrong confidently
