---
title: Genie Agents
type:
  - "[[Technology]]"
  - "[[Product]]"
vendor: "[[Databricks]]"
category: Natural Language Data Interface
formerly: Genie Spaces
tags:
  - genie
  - databricks
---

## Definition

Genie Agents are curated natural-language chat interfaces over approved [[Unity Catalog]] tables. Domain experts configure a set of tables, instructions, and example SQL queries; business users then ask questions in plain language and receive generated SQL results with auto-visualisations. Agents enforce per-user permissions and support conversational follow-ups.

Previously called **Genie Spaces**. Surfaced inside [[Genie One]] and embeddable in external applications via the Conversation API.

## How It Works

1. User asks a natural-language question in the chat UI
2. Genie searches configured tables, instructions, and example SQL
3. Generates SQL, executes against the SQL warehouse
4. Returns results as tables + auto-generated visualisations
5. Maintains conversational context for follow-ups

## Data Access Model

- Queries run via **embedded compute credentials** (warehouse configured by the agent author)
- **[[Unity Catalog]] permissions** enforced per user on results
- Row filters and column masks apply automatically
- Users see only data they are authorised to access — no direct warehouse permissions needed

## Prerequisites

| Requirement | Detail |
|-------------|--------|
| Entitlement | Databricks SQL workspace entitlement |
| Compute | CAN USE on a Pro or Serverless SQL warehouse |
| Data | SELECT on tables to include |
| ACL | CAN EDIT on the agent (creators get CAN MANAGE) |

## Creation Methods

- **UI** — Sidebar → Genie Agents → Create
- **REST API** — `POST /api/2.0/genie/spaces`
- **Databricks SDK** — `w.genie.create(...)`

## Configuration Components

| Component | Description |
|-----------|-------------|
| Tables | [[Unity Catalog]] tables/views exposed to the agent |
| Column configs | Descriptions, synonyms, entity matching, format assistance, exclusions |
| Text instructions | Global guidance for the LLM — keep focused and minimal |
| Example SQL queries | Static or parameterised queries for common questions |
| SQL functions | UC functions for complex, reusable logic |
| Join specs | Pre-defined join relationships between tables |
| SQL snippets | Reusable filters, expressions, measures |
| Sample questions | Suggested questions shown to users in the UI |
| Benchmarks | Ground-truth Q&A pairs for quality scoring |

## Best Practices

### Instructions

- Keep text instructions **focused and minimal** — too many reduce effectiveness
- Prefer **example SQL queries** over text instructions where possible
- Write sample questions the way a **user would naturally phrase them**

### Example SQL Queries

- Focus on logic **unique to your organisation** (not generic SQL)
- Can be **static** or **parameterised** (`:param_name`)
- Parameterised queries produce **verified answers** (trusted assets)
- Supported param types: String, Date, Date and Time, Decimal, Integer

### Column Configuration

- `enable_entity_matching` — for columns with discrete values users might reference by name
- `enable_format_assistance` — for dates, statuses, regions that need format hints
- `exclude` — hide internal or sensitive columns
- `synonyms` — alternative names users might use
- `description` — plain-English explanation of what the column contains

### Join Specs

- Define relationships upfront so Genie doesn't guess
- Include the relationship type annotation in the join SQL

### SQL Functions

- Register complex logic as [[Unity Catalog]] functions
- Reusable across agents and teams
- Add comments describing purpose and sample questions

## Evaluation & Testing

### Built-in Benchmarks

- Add benchmark questions with ground-truth SQL in the agent UI
- Run evaluation → Genie compares generated SQL against expected
- Track accuracy over time via timestamped evaluation runs
- Agent mode uses [[LLM-as-a-Judge]] + evaluation notes (not SQL comparison)

## Integration Patterns

### Embedding in External Apps

- Stateful conversations with follow-ups via the Conversation API
- Build custom chatbot UIs, Slack bots, web apps, internal tools

### Multi-Agent Systems

- Combine Genie (structured data) with RAG agents (unstructured docs)
- Use a supervisor agent to orchestrate
- Supported frameworks: [[LangGraph]], [[DSPy]]
- Deploy on Model Serving or Databricks Apps

### Genie One Integration

- [[Genie One]] searches across all published Genie Agents automatically
- No additional configuration required

### Dashboard Integration

- Dashboards can auto-generate or link Genie Agents
- Follows dashboard credential model (embedded vs viewer credentials)

## Permissions

| Level | Capabilities |
|-------|-------------|
| CAN MANAGE | Full control, delete, manage permissions |
| CAN EDIT | Modify tables, instructions, examples |
| CAN RUN | Ask questions, see responses |
| CAN VIEW | View agent metadata only |

- Share with specific users/groups, all account users, or via shareable link
- External users supported via OpenSharing
- Individual conversations can be shared separately

## Pricing (as of Aug 2026)

- **Free through January 31, 2027** (extended from the original July 31, 2026 cutoff) → pay-as-you-go after. Service principal usage is still billed during the promo, and budget controls don't apply to it.
- Volume file analysis: Foundation Model Serving costs (pay-per-token) + standard Genie usage
- Account admins set budgets; monitor via system billing tables (SKU: `GENIE_FREE_USAGE` during promo)

## Recent Developments

- **2026-08-06** — **Markdown tables in Agent mode APIs** (Beta): table visualizations in the Agent mode API response now return as markdown instead of table-visualization attachments, improving readability for API consumers. Also shipped the same day: longer agent descriptions shown by default, comments on Genie Agent answers from Genie One, and a conversation-mode field (Agent vs. Chat) in the list conversations API. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

## Related

- [[Genie One]] — unified chat that surfaces all Genie Agents
- [[Genie Code]] — developer-focused counterpart
- [[Genie Ontology]] — the org-wide context layer that reduces disambiguation failures and improves first-try accuracy
- [[Knowledge Store]] — the space-level semantic store that extends what Genie knows about a domain
- [[Agent Metadata]] — YAML-defined configuration that shapes how Genie interprets queries
- [[Unity Catalog]] — governance layer enforcing permissions
- [[ThoughtSpot Spotter]] — closest cross-vendor equivalent: ThoughtSpot's conversational analytics agent
- [[Data Quality]] — Gold-layer connection, prompt matching, and benchmarking practices specific to Genie Agents
- [[Evaluation]] — built-in benchmarks and LLM-as-a-Judge scoring used in Genie Agents evaluation
- [[Databricks]] — parent platform
- [[Metric Views]] — governed semantic objects Genie queries instead of raw tables
- [[LangGraph]] — supported multi-agent orchestration framework
- [[DSPy]] — supported multi-agent orchestration framework
- [[Agent Bricks]] — Agent Bricks Supervisor orchestrates Genie Agents as specialized sub-agents
- [[LLM-as-a-Judge]] — used for Agent mode benchmark scoring instead of SQL comparison
