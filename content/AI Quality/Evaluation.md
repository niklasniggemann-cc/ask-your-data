---
title: Evaluation
type: "[[Concept]]"
context: GenAI, Machine Learning
tags:
  - ai-quality
---

## Definition

Evaluation is the process of systematically assessing whether a system produces correct, useful, and trustworthy outputs. In GenAI, it is the **highest-leverage activity** — a tight evaluation loop pays dividends like automated tests in software engineering.

Without evaluation, any improvement to a GenAI system is guesswork. With it, the [[Data Flywheel]] becomes operational.

## Why GenAI Evaluation Is Hard

GenAI evaluation is far more complex than traditional ML:

- **Subjective correctness** — a question often has multiple valid answers; "correct" depends on context and stakeholder expectations
- **Growing evaluation sets** — an initial question set rarely covers the full spectrum of real user queries; the set must expand over time
- **Non-determinism** — identical prompts can yield different outputs across sessions
- **Testing multi-step behavior** — long conversations, tool invocation sequences, and SQL output are not yet reliably testable with standard frameworks
- **Regression risk** — proprietary model vendors optimize continuously; behavior can change without notice

## Evaluation Methods

| Method | Best for |
|--------|---------|
| Exact match / SQL comparison | Deterministic outputs (SQL queries vs. ground truth) |
| Code-based metrics | Heuristics (format checks, length, structure) |
| [[LLM-as-a-Judge]] | Subjective or complex judgments |
| Human review | Ground truth labeling; aligning judges |

## The Evaluation Loop

Evaluation is not a one-time activity. The [[Data Flywheel]] structures it as a continuous loop:

1. Define success metrics (what "good" looks like)
2. Automate measurement against production data
3. Iterate prompts and pipelines based on results

## In Genie Agents

[[Genie Agents]] supports built-in benchmarks: up to 500 questions per space with ground-truth SQL or SQL function references. Benchmark runs produce side-by-side comparisons that are automatically tagged for quick problem identification. Agent Mode uses [[LLM-as-a-Judge]] instead of SQL comparison.

## Related

- [[Data Flywheel]] — the feedback loop evaluation powers
- [[LLM-as-a-Judge]] — key evaluation technique for subjective outputs
- [[MLflow]] — experiment tracking for evaluation results
- [[Genie Agents]] — domain where evaluation is applied concretely
- [[GenAI Technical Debt]] — poor evaluation practices are a primary source of hidden debt
