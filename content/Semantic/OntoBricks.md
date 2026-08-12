---
title: OntoBricks
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Knowledge Graph / Ontology Tool
tags:
  - semantic
  - databricks
  - open-source
---

## Definition

OntoBricks is an open-source Databricks Labs project that transforms Unity Catalog tables into a materialized knowledge graph. It lets teams design ontologies (OWL), map them to Unity Catalog tables via R2RML, materialize the results into a Delta-backed triple store plus a Lakebase Postgres graph engine, reason over the graph (OWL 2 RL, SWRL, SHACL), and query it through an auto-generated GraphQL API and MCP server. It ships as a Databricks App, so the whole pipeline — metadata import through a queryable graph viewer — runs inside the workspace.

Unlike officially supported Databricks products, it's a community/labs project (`databrickslabs` GitHub org) — not GA, not covered by standard Databricks support.

## Key Capabilities

- **Visual ontology design** — define OWL ontologies without hand-writing RDF/OWL syntax
- **R2RML mapping** — maps ontology classes and properties directly to existing Unity Catalog tables
- **Materialized triple store** — triples persist in Delta tables, plus a Lakebase Postgres graph engine for query performance
- **Multi-phase reasoning** — OWL 2 RL forward-chaining deductive closure, SWRL rule evaluation, transitive/symmetric graph expansion, and SHACL constraint validation
- **Auto-generated GraphQL API** — query the resulting knowledge graph without writing SPARQL
- **MCP server** — exposes the graph to LLM agents (Claude Desktop, Cursor, Databricks Playground) via the Model Context Protocol

## Why It's Relevant Here

It sits in the same problem space as [[Semantic Layer]] and Genie Ontology (Databricks' own continuously-learned business-context layer, first covered in the 2026-08-04 update) — turning governed tables into shared, machine-reasonable business meaning — but takes a formal, standards-based approach (OWL/RDF/SHACL) rather than Databricks' proprietary glossary/domains model. It's a useful reference point for how the broader ecosystem is solving the same "ground the AI in real business semantics" problem that [[Natural Language to SQL]] and Genie depend on.

## Recent Developments

**2026-08-05** — Surfaced in the daily briefing as an actively maintained project (199 GitHub stars, 458+ commits) with recent promotion on X/Twitter as a "Digital Twin Builder for Databricks." [Source](https://github.com/databrickslabs/ontobricks)

## Related

- [[Semantic Layer]] — the architectural problem OntoBricks addresses with a formal ontology approach
- [[Unity Catalog]] — the governed metadata foundation OntoBricks maps onto
- [[Lakebase]] — the Postgres graph engine that powers OntoBricks' materialized triple store
- [[Delta Lake]] — the storage layer for OntoBricks' Delta-backed triple store
- [[MCP]] — the protocol OntoBricks uses to expose the graph to agents
- [[Natural Language to SQL]] — the query problem that benefits from grounded semantic/ontology context
