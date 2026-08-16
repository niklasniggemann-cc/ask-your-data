---
title: Hallucinations
aliases:
  - AI Hallucinations
  - LLM Hallucinations
type: "[[Concept]]"
context: GenAI, LLM
tags:
  - semantic
  - ai-quality
---

## Definition

A hallucination is an AI output that is factually incorrect, fabricated, or misleading, presented with the same confidence as accurate information. LLMs don't "know" what is true or false — they optimize for plausible completions based on training patterns. When the model lacks reliable grounding, it generates the most statistically plausible token sequence, which may be entirely fabricated.

The defining characteristic: **confident delivery of wrong information**. Unlike a system that errors out, a hallucinating model answers fluently and with apparent certainty.

## Types

| Type | Description |
|------|-------------|
| **Factuality errors** | States incorrect facts about the world |
| **Faithfulness errors** | Distorts or misrepresents the source or prompt |
| **Fabrication** | Invents plausible-sounding details — URLs, citations, SQL column names — that don't exist |
| **Conflation** | Blends two real concepts into one incorrect composite answer |

## Why It's Hard to Fix

Hallucinations arise from the fundamental way LLMs work: they predict plausible completions, not verified facts. The model is rewarded during training for generating fluent responses, not for acknowledging the limits of its knowledge.

In data analytics, the failure mode is particularly dangerous: the model generates a plausible SQL query, business metric, or analytical insight that is subtly or significantly wrong — presented as confidently as a correct answer. This is the **Garbage In, Confident Garbage Out** pattern.

## In the Data Analytics Context

Pure [[Natural Language to SQL]] systems are especially vulnerable: when the model infers business logic from column names rather than governed definitions, it can generate queries that are syntactically valid but semantically wrong.

The [[Semantic Layer]] is the primary structural defense: when the LLM queries governed [[Metric Views]] rather than raw tables, business logic is enforced by construction rather than inferred. [[Agent Metadata]] synonyms make term resolution deterministic, removing the guesswork that produces hallucinations.

## Mitigation

| Approach | Mechanism |
|----------|-----------|
| **[[Semantic Layer]]** | LLM queries governed definitions, not raw tables |
| **[[Agent Metadata]]** | Synonyms make term resolution deterministic |
| **[[RAG]]** | Grounds responses in retrieved, verifiable source documents |
| **[[LLM-as-a-Judge]]** | Detects hallucinated responses via automated scoring |
| **[[Evaluation]]** | Systematic measurement catches hallucinations before users see them |
| **[[Observability]]** | Makes hallucination-producing calls visible and diagnosable |
| **[[Genie Ontology]]** | Reduces disambiguation failures — a major hallucination trigger — via organizational context |

## Related

- [[Natural Language to SQL]] — the query context where hallucinations surface as wrong results
- [[Semantic Layer]] — structural defense against hallucinated metric definitions
- [[Agent Metadata]] — deterministic term resolution that removes inference guesswork
- [[LLM-as-a-Judge]] — evaluation technique for detecting hallucinated responses
- [[Data Flywheel]] — the feedback loop that surfaces and corrects hallucinations over time
- [[RAG]] — retrieval-based grounding that reduces hallucinations on document questions
- [[Genie Ontology]] — reduces disambiguation failures, a major hallucination trigger, via organizational context
- [[Evaluation]] — systematic measurement catches hallucinations before users see them
