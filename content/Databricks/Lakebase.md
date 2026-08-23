---
title: Lakebase
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Serverless Postgres Database
tags:
  - databricks
---

## Definition

Lakebase is Databricks' fully managed, serverless Postgres database designed as the working-memory and operational-data layer for AI agents and applications. It provides low-latency read/write access for agent state, conversational memory, and operational workloads — integrated with the lakehouse for analytical queries on the same data. Generally Available as of 2026.

## Why Postgres

Postgres compatibility means agents and applications use standard Postgres drivers, SQL, and tooling — no Databricks-specific SDK required. Lakebase adds lakehouse integration, [[Unity Catalog]] governance, and serverless scaling on top of the Postgres surface.

## Architecture

- **Serverless** — Postgres engine backed by cloud object storage; scales to zero when idle, no capacity provisioning required
- **Tiered storage** — hot data in RAM/local NVMe cache, cold data in object storage; indexes survive scale-to-zero without a warmup penalty
- **Lakehouse integration** — operational data in Lakebase is queryable alongside [[Delta Lake]] analytics tables through the same [[Unity Catalog]] governance layer

## Agent Use Cases

| Use Case | How Lakebase Fits |
|----------|------------------|
| Conversational memory | Persist session history across calls without external infra |
| Agent state | Store intermediate results, task queues, coordination state |
| Retrieval | [[Lakebase Search]] — hybrid vector + full-text natively on Postgres |
| Operational writes | Low-latency transactional writes needed during an agent reasoning loop |

## Managed Memory for Agents

[[Agent Bricks]] uses Lakebase as the backend for managed agent memory. Agents persist context and session history as governed Postgres tables — queryable via SQL, auditable through Unity Catalog, and accessible across sessions without custom state management infrastructure.

## Lakebase vs. Delta Lake

| | Lakebase | [[Delta Lake]] |
|--|---------|-------------|
| Workload | OLTP (low-latency read/write) | OLAP (batch analytics) |
| Interface | Postgres SQL | Spark / Databricks SQL |
| Latency | Milliseconds | Seconds to minutes |
| Use case | Agent memory, operational apps | Medallion pipelines, BI |

Both are governed in Unity Catalog and can be queried together.

## Recent Developments

- **Lakebase Postgres APIs reach GA** (Aug 14, 2026) — programmatic management of Lakebase Postgres (projects, branches, endpoints, databases, roles, credentials, synced tables, catalogs) is now generally available via REST API, Databricks CLI, and Databricks SDKs (Python, Java, Go). Some individual operations remain in Beta — the Postgres API reference marks status per-operation. [Source](https://docs.databricks.com/aws/en/oltp/projects/api-usage)
- **Compliance security profile support** (Aug 5, 2026) — Lakebase is now available by default for workspaces with the compliance security profile enabled, including HIPAA, C5, or TISAX controls (or the profile with no standard selected) — removes a deployment blocker for agent-memory workloads in regulated environments. [Source](https://docs.databricks.com/aws/en/oltp/projects/data-protection)
- **Electric (maker of PGlite) acquired to bring WASM Postgres to AI agent sandboxes** (Aug 11, 2026) — Electric's PGlite (a WASM build of Postgres, 13M weekly downloads) now gives each individual agent sandbox its own local Postgres instance for ultra-low-latency context, while Electric's real-time sync engine keeps that distributed state synchronized back to a central Lakebase. Extends Lakebase from a single serverless Postgres endpoint into a two-tier model: local WASM Postgres at the edge (in the sandbox where an agent runs) plus centralized Lakebase for shared/durable state. [Source](https://www.databricks.com/blog/electric-joins-databricks-bring-wasm-postgres-ai-agent-sandboxes)

## Related

- [[Lakebase Search]] — hybrid vector + full-text retrieval built into Lakebase Postgres
- [[Agent Bricks]] — uses Lakebase for managed memory and agent state
- [[Delta Lake]] — analytical complement; Lakebase handles OLTP, Delta handles OLAP
- [[Unity Catalog]] — governs Lakebase instances and data like any other Databricks asset
- [[Databricks]] — parent platform
