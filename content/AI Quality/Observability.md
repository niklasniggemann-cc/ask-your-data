---
title: Observability
type: "[[Concept]]"
context: Platform Engineering, GenAI
tags:
  - ai-quality
---

## Definition

Observability is the practice of instrumenting a system so that its internal state can be understood from its external outputs. In GenAI pipelines, observability means making the inputs, outputs, and behavior of each intermediate LLM call visible enough to diagnose failures — not just detect that something went wrong.

Enabling tracing alone is not enough. Proper observability requires structured instrumentation with a framework that captures context alongside each call.

## Why It's Critical in GenAI

When a GenAI response is wrong, finding the root cause requires examining intermediate LLM calls — which specific prompt produced which intermediate output, which tool was called with which parameters. Without observability:

- Debugging becomes guesswork
- Guesswork compounds into [[GenAI Technical Debt]] (the Opaque Pipelines category)
- Fixes address symptoms, not root causes

## What to Instrument

- **LLM calls** — prompt sent, model used, response received, latency, token count
- **Tool invocations** — tool name, parameters, return value
- **Retrieval steps** — query used, documents retrieved, relevance scores
- **Scores** — [[LLM-as-a-Judge]] scores and rationales for each call

## Observability vs. Monitoring

| | Observability | Monitoring |
|--|--------------|-----------|
| Focus | Diagnosing unknown failures | Alerting on known failure modes |
| Approach | Structured traces, spans | Dashboards, threshold alerts |
| When useful | Debugging specific bad responses | Detecting regressions at scale |

Both are needed. Observability enables debugging; monitoring enables alerting.

## In the Data Flywheel

Observability is a prerequisite for [[Data Flywheel]] step two (Automate Measurement): you cannot measure quality you cannot see. It is also how production data is sampled for human review and [[LLM-as-a-Judge]] scoring.

## Related

- [[GenAI Technical Debt]] — opaque pipelines are one of the four debt categories
- [[Data Flywheel]] — observability enables automated measurement
- [[LLM-as-a-Judge]] — often deployed as part of the observability pipeline
- [[MLflow]] — one tool for tracking and visualizing observed data
