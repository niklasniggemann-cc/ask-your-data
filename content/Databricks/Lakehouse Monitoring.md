---
title: Lakehouse Monitoring
type: "[[Technology]]"
vendor: "[[Databricks]]"
category: Data Quality Monitoring
tags:
  - databricks
---

## Definition

Lakehouse Monitoring is a Databricks tool for tracking data quality and model drift across the platform. It monitors the six [[Data Quality]] dimensions by creating metric tables and auto-generated dashboards that visualize quality metrics over time.

## How It Works

- Attach a monitor to a [[Delta Lake]] table
- Databricks automatically creates a metric table alongside it
- An auto-generated dashboard visualizes quality metrics (freshness, completeness, distribution drift, etc.)
- Metrics track over time — enabling trend analysis, not just point-in-time snapshots

## What It Monitors

- **Data quality** — consistency, completeness, accuracy, validity, uniqueness, timeliness
- **Model drift** — for ML inference tables; tracks distribution shifts between baseline and production
- **Custom metrics** — user-defined SQL expressions evaluated alongside built-in metrics

## Related

- [[Data Quality]] — the six dimensions Lakehouse Monitoring tracks
- [[Delta Lake]] — the table format being monitored
- [[Databricks]] — platform
- [[Medallion Architecture]] — the layer structure within which monitoring is applied
