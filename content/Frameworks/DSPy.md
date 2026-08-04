---
title: DSPy
type: "[[Technology]]"
category: LLM Programming Framework
license: Open Source (MIT)
origin: Stanford NLP
tags:
  - framework
---

## Definition

DSPy (Declarative Self-improving Python) is a framework from Stanford NLP for programming with language models. Rather than hand-crafting prompts, developers write programs using typed signatures and declarative modules — and DSPy handles prompt generation, few-shot example selection, and optimization automatically.

## Core Idea

In DSPy, you define *what* a module should do (input/output signature) rather than *how* to prompt for it. An optimizer (like MIPRO or BootstrapFewShot) then compiles the program into effective prompts, given a dataset of input/output examples and a metric to optimize.

```python
class GenerateSQL(dspy.Signature):
    """Convert a natural language question to SQL."""
    question: str = dspy.InputField()
    sql: str = dspy.OutputField()
```

## Key Concepts

- **Signatures** — typed input/output declarations; the interface contract for each module
- **Modules** — composable building blocks (`dspy.Predict`, `dspy.ChainOfThought`, `dspy.ReAct`)
- **Optimizers** — automatically improve prompts and few-shot examples given a metric
- **Teleprompters** — the original name for optimizers; still used in some docs

## Use Case in Multi-Agent Systems

In a [[Genie Agents]] multi-agent architecture, DSPy can be used to build and optimize the modules that route between Genie (structured SQL queries) and RAG agents (unstructured documents) — without manually crafting routing prompts.

## Related

- [[LangGraph]] — alternative framework focused on stateful graph-based orchestration
- [[Genie Agents]] — one tool in a DSPy-orchestrated multi-agent system
