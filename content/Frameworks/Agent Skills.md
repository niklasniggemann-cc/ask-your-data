---
title: Agent Skills
aliases:
  - Databricks Agent Skills
  - databricks-agent-skills
type:
  - "[[Technology]]"
  - "[[Standard]]"
vendor: "[[Databricks]]"
category: AI Coding Assistant Tooling
tags:
  - framework
  - databricks
---

## Definition

Agent Skills are task-specific instruction files — Markdown with front-matter metadata — that AI coding assistants (Claude Code, GitHub Copilot, Cursor) load to perform development tasks more effectively. They follow the open [Agent Skills](https://agentskills.io/) standard. Databricks publishes an officially maintained skill repository, `databricks/databricks-agent-skills`, distributed through the Databricks CLI so assistants can work with Databricks-specific resources (bundles, jobs, SQL, and more) out of the box.

## Key Properties

- Each skill is a Markdown file with front-matter describing when and how it should be used
- AI coding assistants discover and load relevant skills automatically based on the task at hand
- Installed via `databricks aitools install` (auto-detects supported agents), or scoped to a single project instead of globally
- Skills from arbitrary GitHub repos (not distributed via the Databricks CLI) can be pulled in with the community **Skills CLI** (Vercel Labs), an open-source package manager for agent skills

## Databricks Skill Repositories

- **Databricks agent skills** (official) — covers Agent Bricks, AI Functions, AI/BI Dashboards, Databricks Apps, Bundles, Databricks CLI, Databricks Lakehouse, Genie, Iceberg, Lakebase, Lakeflow Jobs, Metric Views, MLflow evaluation, Model Serving, Python SDK, Lakeflow pipelines, serverless migration, Structured Streaming, synthetic data, Unity Catalog, AI Search, and Zerobus ingest
- **AI Dev Kit skills** — deprecated community set, superseded by the official repo above
- **Databricks app template skills** — embedded in app templates for LangGraph/LangChain/OpenAI Agents SDK agents and Streamlit/Dash/Gradio/Shiny/Flask/Node.js data apps
- **MLflow skills** — instrumenting, debugging, and evaluating LLM agents with MLflow

## In the Genie Code Context

Full page [[Genie Code]] (GA August 2026) lets users personalize its behavior with skills, instructions, and MCP servers. The same Agent Skills mechanism that powers external coding assistants extends to Databricks' own in-workspace assistant, not just third-party tools.

## Recent Developments

**2026-08-06** — Databricks published the officially maintained `databricks/databricks-agent-skills` GitHub repo and the `databricks aitools` CLI command group, packaging Databricks-specific development knowledge as Agent Skills for Claude Code, GitHub Copilot, and Cursor. [Source](https://docs.databricks.com/aws/en/agent-skills/)

## Related

- [[Genie Code]] — Databricks' own coding assistant, extensible via the same skill mechanism
- [[MCP]] — complementary open standard for live tool connectivity; Agent Skills packages instructions rather than runtime tool access
- [[MLflow]] — publishes its own skill set for agent evaluation and observability workflows
- [[Databricks]] — platform
