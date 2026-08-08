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

## Related

- [[Data Flywheel]] — the feedback loop MLflow tracking enables
- [[LLM-as-a-Judge]] — evaluation technique whose scores MLflow stores
- [[Evaluation]] — broader concept
- [[Databricks]] — platform where MLflow is natively integrated
