---
title: Data Flywheel
type: "[[Concept]]"
context: GenAI, Product Engineering
also-known-as: Learning Loop, Feedback Loop
tags:
  - ai-quality
---

## Definition

The Data Flywheel is a closed feedback loop that turns a deployed GenAI system's output into systematic quality improvement. It moves an application from a static asset toward a continuously learning system. Teams that ship without one are running a **hope-driven deployment** — quality debt accumulates silently until a model update or user behavior shift exposes it.

## Three Steps

### 1. Define Success Metrics

- Cannot be derived by theorizing alone — examine actual production data first
- **Code-based metrics**: simple functions for heuristics
- **[[LLM-as-a-Judge]]**: for subjective or complex judgments; provide examples to align the judge's output with your own
- **Binary metrics** are much easier to align than graded ones
- Validate input data as well as output data (Postel's Law: conservative in what you send, liberal in what you accept)

### 2. Automate Measurement

- Keep defined metrics aligned with production data — as automated as possible
- Periodically reassess whether chosen metrics still align with goals (LLM APIs change under the hood)
- An agent that regularly analyzes labeled production data can flag when the metric set needs updating
- Main challenge: regular human labeling for each metric — important but burdensome

### 3. Iterate to Improve

- Combine manual human insight with automated techniques
- Iterate prompts and pipelines by hand to lift metric scores
- Review metric scores regularly to spot patterns or clusters of low-performing instances
- Analyze distribution of input data to detect shifts in user behavior
- Automate pipeline improvements in response to metrics where possible

## The Human Side

- Schedule time with domain experts
- Build rubrics to reconcile differences in assessment — in-person workshops usually required
- Only once human annotators are aligned can their evaluations be folded into [[LLM-as-a-Judge]]
- Not all feedback carries equal weight — negotiate priorities and educate on LLM limits
- Frequent stakeholder touchpoints turn critics into collaborators

## Why It Matters

Evaluation in GenAI systems is the highest-leverage activity, analogous to automated tests in software engineering: significant upfront investment, massive long-term dividends. Without the flywheel, any improvement to a GenAI system is guesswork.

## Related

- [[GenAI Technical Debt]] — the debt categories the flywheel addresses
- [[LLM-as-a-Judge]] — key technique in step one
- [[Evaluation]] — broader concept
- [[Genie Agents]] — one concrete application domain
