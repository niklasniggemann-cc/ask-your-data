---
title: Omnigent
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Agent Meta-Harness
license: Open Source (Apache 2.0)
tags:
  - databricks
  - framework
---

## Definition

Omnigent is an open-source (Apache 2.0) meta-harness that sits above individual agent frameworks — Claude Code SDK, Codex, Pi, OpenAI Agents — to compose, govern, and share agents from a unified layer. Released June 2026 by Databricks. It enforces guardrails **structurally** at the harness level rather than via prompt instructions an agent could reason around.

Databricks also offers a fully managed hosted version.

## The Meta-Harness Concept

Individual agent frameworks (Claude Code, LangGraph, OpenAI Agents) each manage their own lifecycle. Omnigent wraps them all as a new abstraction layer: instead of choosing one framework, teams can mix harnesses and switch between them with `--harness flag` without rewriting agent code. The governance layer — cost budgets, permissions, sandboxing — stays consistent regardless of which framework runs underneath.

## Key Capabilities

### Agent Interoperability
Combine multiple models and harnesses in one deployment. Supported: Claude Code SDK, Codex, Pi, OpenAI Agents, Open Responses, and custom harnesses. Switch with `--harness` flag — one-line change, no code rewrite.

### Stateful Governance
Cost budgets and permissions enforced at the meta-harness level, not via prompts. A budget limit is a hard constraint; an allowed path is a sandboxed OS-level permission. Neither can be overridden by agent reasoning.

### Live Session Sharing
Share a live agent session via URL. Teammates join to review, comment, and steer the agent in real time — useful for auditing agentic work or collaborative debugging.

### Filesystem and Network Sandboxing
Restricts what agents can read, write, or call without requiring agents to police themselves. Addresses a governance gap in purely prompt-based guardrails.

## Governance Approach

| | Prompt-based guardrails | Omnigent structural governance |
|--|------------------------|-------------------------------|
| Enforcement | Agent must follow instructions | Harness-level hard limit |
| Auditability | Depends on tracing setup | Tracked with full action context |
| Override risk | Agent can reason around prompts | Cannot be overridden |

## Status

Early software — v0.1.1 as of June 2026, Apache 2.0. Community/labs project with Databricks backing. Not yet GA.

## Related

- [[Agent Bricks]] — Databricks' governed agent platform; Omnigent sits above it
- [[MCP]] — protocol Omnigent-governed agents use to connect to external tools and data
- [[Unity Catalog]] — governance layer within which Omnigent-managed agents operate
- [[LangGraph]] — one of the frameworks Omnigent can wrap
- [[MLflow]] — observability layer alongside Omnigent for tracing
