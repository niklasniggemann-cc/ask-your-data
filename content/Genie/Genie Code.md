---
title: Genie Code
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: AI Coding Assistant
tags:
  - genie
  - databricks
---

## Definition

Genie Code is [[Databricks]]' AI coding assistant for developers and data practitioners, deeply integrated into the workspace. It is context-aware via [[Unity Catalog]] — understanding tables, columns, and lineage — and adapts its capabilities based on the current product surface.

## Surface-Specific Capabilities

| Surface | Genie Code focus |
|---------|-----------------|
| Lakeflow Pipelines Editor | Pipeline editing and data engineering |
| Notebooks / SQL Editor | Data exploration and analysis |
| Dashboards | Data analysis and dashboard creation |
| Notebooks on AI Runtime | Deep learning training/fine-tuning code, environment debugging, GPU workload troubleshooting |

## Core Capabilities

- Inline suggestions and quick fixes
- Error diagnosis
- Sample data exploration
- Multi-step agentic tasks — handles complex requests autonomously
- Creates [[Genie Agents]] from a natural-language description
- Personalizable via [[Agent Skills]], instructions, and MCP servers (Full page Genie Code, GA August 2026)
- Searches the public web to answer questions needing current information, citing sources (Beta, August 2026 — disabled by default, workspace admin must enable via Previews)

## Unity Catalog Integration

Genie Code reads table and column metadata, descriptions, and lineage from [[Unity Catalog]], so suggestions are grounded in the actual data structure rather than generic patterns.

## Recent Developments

- **2026-09-01** — **Scheduled tasks reach GA**: Genie Code can run a prompt on a recurring schedule, with each run executing as a full Genie Code session that produces a continuable chat with the results. Create one by describing the schedule in chat, or manually via the Scheduled tasks pane. Distinct from running as a Lakeflow Jobs task (below) — this is Genie Code driving its own recurring schedule rather than being invoked as a pipeline step. [Source](https://docs.databricks.com/aws/en/genie-code/scheduled-tasks)
- **2026-08-27** — **Genie Code for AI Runtime** (Public Preview): inside notebooks connected to AI Runtime's on-demand serverless GPUs (A10s/H100s), Genie Code can generate distributed training code, resolve library/environment/dependency errors, suggest performance optimizations, and debug convergence issues and cryptic framework errors. Extends Genie Code from data engineering/SQL/dashboards into GPU-based deep learning training and fine-tuning. [Source](https://docs.databricks.com/aws/en/machine-learning/ai-runtime/genie-code)
- **2026-08-27** — **Genie Code as a Lakeflow Jobs task** (Beta): Genie Code can now run as a task inside a [[LakeFlow]] Job, executing a prompt autonomously, reading upstream task outputs, and calling tools as needed; the task returns a link to the resulting conversation. Turns Genie Code from an interactive assistant into an orchestrable pipeline step. [Source](https://docs.databricks.com/aws/en/jobs/tasks/genie-code)
- **2026-08-19** — **Select a level of effort**: a new selector in the prompt box lets you choose how Genie Code balances response quality and cost per conversation — **Auto** (default, highest quality) or **Low** (cheaper, for simpler tasks). Workspace chat only. [Source](https://docs.databricks.com/aws/en/genie-code/use-genie-code#select-a-level-of-effort)
- **2026-08-14** — **File uploads**: you can now upload files to Genie Code to use as context for the current chat. [Source](https://docs.databricks.com/aws/en/genie-code/use-genie-code#attach-files)

## Related

- [[Genie One]] — unified chat that Genie Code operates alongside
- [[Genie Agents]] — agents that Genie Code can create and review
- [[Unity Catalog]] — source of schema and lineage context
- [[Agent Skills]] — the mechanism Genie Code uses for personalization
- [[Genie App Builder]] — sibling Genie-family product for building governed data apps via a low-code surface
- [[Genie ZeroOps]] — sibling Genie-family product for autonomous data/AI operations
- [[Databricks]] — platform
