---
title: GenAI Technical Debt
type: "[[Concept]]"
context: Generative AI, Platform Engineering
tags:
  - ai-quality
---

## Definition

GenAI technical debt refers to the categories of engineering debt specific to generative AI systems — distinct from traditional ML or software debt. It is easy to overlook, compounds quickly, and is not always visible until a model update or user behavior shift exposes it.

## Where GenAI Effort Actually Goes

GenAI project effort distribution differs from traditional ML:

| Activity | Traditional ML | GenAI |
|----------|----------------|-------|
| Data collection | Dominant | Often easier (context docs, manuals) |
| Evaluation | Straightforward metrics | **Dominant** — subjective, complex, time-consuming |
| Monitoring | Standard | Real-time inference analysis pipelines + alerting |
| Testing | Unit/integration | Much harder — multi-turn conversations, SQL output, tool invocation |

Additional pressures unique to GenAI:
- Evaluation set must grow over time as real user queries are observed
- Proprietary model vendors continuously optimize — the "model" is a **service prone to regressions**
- Evaluation criteria must account for non-frozen weights
- More stakeholder meetings required — response quality depends heavily on end-user expectations

## The Four Debt Categories

### 1. Tool Sprawl

- Tools extend LLM capabilities but become harder to manage as their number grows
- **Quality degradation**: the model must select the right tool from a large set — error-prone when tools overlap
- Overlapping parameter structures across similar tools compounds selection errors
- Defense: be **strategic and minimal** about tool adoption

### 2. Prompt Complexity

- Long prompts invite contradictory directives and stale information
- Common anti-pattern: only append to prompts over time, never refactor
- Different developers and domain experts add instructions without revising existing ones
- Better approach: **break into smaller, focused prompts** — clarity, accuracy, and troubleshooting all improve
- Use frameworks that track prompt versions and enforce expected inputs/outputs

### 3. Opaque Pipelines

- When a response is wrong, identifying the relevant intermediate LLM call is time-consuming
- Enabling tracing alone is insufficient
- Requires proper instrumentation with **[[Observability]]** tooling and a structured framework
- Without it: debugging becomes guesswork → guesswork compounds into debt

### 4. Missing [[Data Flywheel]]

- A team that ships without measuring success runs a **hope-driven deployment**
- Without feedback loops, quality debt accumulates silently until a model update exposes it
- The [[Data Flywheel]] is the structured solution

## Why GenAI Debt Is Different

| Dimension | Traditional Software | GenAI |
|-----------|---------------------|-------|
| Testing | Unit/integration tests | Multi-turn conversations, SQL output, tool invocation — not yet reliably testable |
| Monitoring | Standard metrics | Subjective feedback; LLM-based evaluation pipelines |
| Dependencies | Versioned libraries | Model-as-a-service; weights not frozen, behavior changes without notice |
| Failure mode | Explicit errors | Confident-sounding wrong answers |

## Related

- [[Data Flywheel]] — structured solution to the missing feedback loop category
- [[Observability]] — addresses opaque pipelines
- [[LLM-as-a-Judge]] — evaluation technique used to measure quality
