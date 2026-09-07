---
title: MLflow
type: "[[Technology]]"
category: ML Lifecycle Platform
license: Open Source (Apache 2.0)
tags:
  - framework
---

## Definition

MLflow is an open-source platform for managing the full ML lifecycle: experiment tracking, model packaging, model registry, and deployment. In the context of GenAI and [[Genie Agents]] evaluation, it is used to track evaluation results across runs — making quality trends visible over time.

## Core Components

- **Tracking** — log parameters, metrics, and artifacts for each experiment run
- **Model Registry** — versioned model storage with staging and production lifecycle
- **Projects** — reproducible packaging of ML code
- **Deployments** — model serving across multiple targets

## In GenAI Evaluation

MLflow's experiment tracking is the natural store for [[Data Flywheel]] evaluation results:

- Each evaluation run is an MLflow experiment
- [[LLM-as-a-Judge]] scores are logged as metrics per question
- Runs are compared across time to track quality trends
- `mlflow.genai` module provides helpers for LLM-specific evaluation patterns

## Integration with Databricks

MLflow is built into [[Databricks]] — no separate installation required. Experiments are managed within the workspace and linked to Unity Catalog for governance. Storing MLflow 3 traces in Unity Catalog tables — already the recommendation for new/production workloads — is set to become the default for workspaces with the compliance security profile enabled, rolling out mid-August 2026.

## Recent Developments

- **2026-08-12** — **Custom trace views** in the MLflow trace explorer (Beta) — describe the layout you want in plain language, and [[Genie Agents|Genie]] generates a reusable view surfacing the trace fields, metrics, and feedback controls most relevant to your review workflow. [Source](https://docs.databricks.com/aws/en/mlflow3/genai/tracing/observe-with-traces/custom-trace-view)

## Related

- [[Data Flywheel]] — the feedback loop MLflow tracking enables
- [[LLM-as-a-Judge]] — evaluation technique whose scores MLflow stores
- [[Evaluation]] — broader concept
- [[Databricks]] — platform where MLflow is natively integrated
- [[Observability]] — MLflow tracing is one tool for tracking and visualizing observed data
- [[Agent Bricks]] — uses MLflow for observability and tracing of Agent Bricks deployments
- [[Lakebase Search]] — MLflow traces and agent observability often sit alongside Lakebase-backed agent memory
- [[Agent Skills]] — publishes its own skill set for agent evaluation and observability workflows with MLflow
- [[Omnigent]] — MLflow is a common observability layer alongside Omnigent-managed agents
