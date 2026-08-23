---
title: LLM-as-a-Judge
type: "[[Concept]]"
context: GenAI, Evaluation
tags:
  - ai-quality
---

## Definition

LLM-as-a-Judge is an evaluation technique where a language model scores the outputs of another LLM (or the same model) against defined criteria. Used when evaluation requires subjective or complex judgment that cannot be expressed as a simple code-based metric — such as assessing whether a natural language response is accurate, helpful, or faithful to a source.

It is a core component of the [[Data Flywheel]]: step one (Define Success Metrics) relies on LLM-as-a-Judge when human judgment cannot be automated directly.

## Why It's Needed

Traditional evaluation metrics (exact match, BLEU, F1) fail for generative outputs where multiple correct answers exist or correctness is contextual. Human evaluation is the gold standard but doesn't scale. LLM-as-a-Judge bridges the gap: scalable, automatable, and adaptable to domain-specific criteria.

## Key Challenges

- **Judge alignment** — the judge's output must be calibrated to match human judgment; providing few-shot examples significantly improves alignment
- **Binary vs. graded metrics** — binary metrics (correct/incorrect) are much easier to align than graded scales (1–5); prefer binary where possible
- **Judge drift** — as the underlying model updates (model-as-a-service), the judge's behavior may change; periodic recalibration needed
- **Self-evaluation bias** — a model judging its own outputs may be systematically overconfident

## In Practice

The judge is typically a more capable or differently-prompted model than the one being evaluated. It receives the question, the system output, and optionally a reference answer, then returns a score and rationale. [[MLflow]] `mlflow.genai` provides helpers for LLM-based evaluation patterns.

For [[Genie Agents]] benchmark runs in Agent Mode, LLM-as-a-Judge is used instead of SQL comparison (since agent mode produces narrative responses, not raw SQL).

## Related

- [[Data Flywheel]] — the feedback loop LLM-as-a-Judge enables
- [[Evaluation]] — broader concept
- [[MLflow]] — used to track LLM-as-a-Judge scores across runs
- [[Genie Agents]] — applied in Agent Mode benchmarks
- [[GenAI Technical Debt]] — evaluation technique used to measure quality and manage debt
- [[Observability]] — makes the calls LLM-as-a-Judge scores visible and diagnosable
- [[Hallucinations]] — the primary failure mode LLM-as-a-Judge is used to detect
