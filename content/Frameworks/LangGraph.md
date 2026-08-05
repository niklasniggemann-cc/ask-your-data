---
title: LangGraph
type: "[[Technology]]"
category: Agent Orchestration Framework
license: Open Source (MIT)
tags:
  - framework
---

## Definition

LangGraph is a graph-based framework for building stateful, multi-step AI agents. It models agent workflows as directed graphs — nodes are processing steps, edges define the flow of control — enabling complex reasoning patterns like cycles, branching, and human-in-the-loop pauses.

## Core Concepts

- **Nodes** — individual processing steps (LLM calls, tool use, data retrieval)
- **Edges** — transitions between nodes; can be conditional
- **State** — a typed dictionary passed between nodes and accumulated across the graph
- **Cycles** — unlike linear chains, LangGraph supports loops for iterative refinement

## Use Case in Multi-Agent Systems

In a [[Genie Agents]] multi-agent architecture, LangGraph is used to orchestrate a supervisor agent that routes between:
- Genie (structured, governed SQL queries over [[Unity Catalog]] data)
- RAG agents (unstructured document retrieval)
- Other specialized tools

The supervisor decides which worker to invoke and how to combine their outputs into a coherent response.

## Related

- [[Genie Agents]] — one worker in a LangGraph multi-agent system
- [[Agent Bricks]] — Databricks' governed agent platform; uses LangGraph as one of its supported frameworks
- [[Omnigent]] — meta-harness that sits above LangGraph to govern cross-framework agent compositions
- [[DSPy]] — alternative framework for LLM program composition
