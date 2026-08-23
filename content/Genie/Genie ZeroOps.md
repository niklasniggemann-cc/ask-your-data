---
title: Genie ZeroOps
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Autonomous Data/AI Operations
tags:
  - genie
  - databricks
---

## Definition

Genie ZeroOps is [[Databricks]]' autonomous background agent for data and AI operations. It monitors pipelines, jobs, tables, and ML models, investigates issues on its own, and proposes — or applies — fixes, aiming to eliminate routine DBA and DataOps toil rather than just surfacing alerts for a human to act on.

## Core Capabilities

- Monitors pipelines, tunes queries, provisions infrastructure, queries inference tables, and runs root-cause analysis on alerts
- **Shallow-clones** production data (a metadata-only table clone with no data duplication) into an isolated environment to validate a proposed fix against real data without touching production
- Applies permission guardrails and network isolation to that isolated validation environment
- Initial scope: jobs, pipelines, tables, and ML workloads — apps and [[Lakebase]] databases are on the roadmap

## Status

Announced at Data + AI Summit 2026 (June 16–17) alongside [[Genie App Builder]]; entered private preview shortly after, starting with jobs/pipelines/tables/ML support. Still in private preview as of August 2026, with no GA date announced.

## Related

- [[Genie App Builder]] — sibling Genie-family product from the same DAIS 2026 announcement
- [[Lakebase]] — on ZeroOps's roadmap for future database support
- [[LakeFlow]] — the pipelines ZeroOps monitors and tunes
- [[Databricks]] — platform
- [[Genie Code]] — sibling Genie-family product, developer-focused AI coding assistant
- [[Genie One]] — sibling Genie-family product, unified chat surface across all agents
