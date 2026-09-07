---
title: Agent Metadata
type:
  - "[[Concept]]"
  - "[[Technology]]"
vendor: "[[Databricks]]"
category: Semantic Metadata
requires: Databricks Runtime 17.3, YAML version 1.1
governed-in: "[[Unity Catalog]]"
tags:
  - databricks
  - semantic
---

## Definition

Agent Metadata is a YAML-defined specification in [[Unity Catalog]] that attaches structured business context to [[Metric Views]] through three mechanisms: **display names**, **synonyms**, and **format specifications**. It is governed within [[Unity Catalog]] and automatically consumed by downstream tools including dashboards and AI assistants like [[Genie Agents]].

It does not make inference possible — LLMs can often already infer meaning from column names. It makes resolution **deterministic, consistent, and governed at scale**.

## When Inference Is Sufficient (and When It Isn't)

On a small, well-structured table with recognizable abbreviations, LLM inference often produces correct results without any metadata. The value of Agent Metadata becomes apparent when:

- A schema has **hundreds of columns** — probability of incorrect resolution increases proportionally
- **Multiple columns are plausible matches** for a single query (e.g., five `rev_*` columns when the user asks about "revenue")
- **Different departments use divergent terminology** for the same metric — Finance says "net retention", Product says "expansion revenue"

## The Three Mechanisms

### 1. Display Names

Replace technical column identifiers with human-readable labels across all downstream surfaces. `rev_mrr_usd` becomes **Monthly Recurring Revenue** in every dashboard and AI response.

### 2. Synonyms

Explicit term-to-column mappings that make resolution deterministic. Up to **10 synonyms per dimension or measure**, up to 255 characters each.

Example: `pct_cust_attrit_q` mapped to synonyms: "churn", "attrition rate", "customer churn", "churn rate" — any of these resolves to the correct measure regardless of model version or phrasing.

### 3. Format Specifications

Defines how values are rendered in visualization tools, propagated automatically to all dashboards built on the metric view:
- `type: percentage` → renders `0.034` as `3.4%`
- `type: currency` with `currency_code: USD` → renders `48250.00` as `$48,250.00`
- `type: number` with `decimal_places: 0` → renders integers without decimals

## YAML Structure

```yaml
version: 1.1

source: analytics.saas.subscription_metrics

dimensions:
  - name: dt_cohort_start
    expr: dt_cohort_start
    display_name: 'Cohort Start Date'
    synonyms:
      - signup date
      - cohort date
      - when they signed up

  - name: plan_tier
    expr: plan_tier
    display_name: 'Plan Tier'
    synonyms:
      - pricing plan
      - subscription level
      - plan type

measures:
  - name: rev_mrr_usd
    expr: SUM(rev_mrr_usd)
    display_name: 'Monthly Recurring Revenue'
    synonyms:
      - MRR
      - monthly revenue
      - recurring revenue
    format:
      type: currency
      currency_code: USD
      decimal_places:
        type: exact
        places: 2

  - name: pct_cust_attrit_q
    expr: AVG(pct_cust_attrit_q)
    display_name: 'Quarterly Churn Rate'
    synonyms:
      - churn
      - attrition rate
      - customer churn
      - churn rate
    format:
      type: percentage
      decimal_places:
        type: exact
        places: 1
```

## Presentation Impact

Even when inference resolves the correct column, output quality differs:

**Without Agent Metadata:**

| pct_cust_attrit_q | region_code |
|-------------------|-------------|
| 0.034 | NA |
| 0.051 | EMEA |

**With Agent Metadata:**

| Region | Quarterly Churn Rate |
|--------|---------------------|
| 3.4% | NA |
| 5.1% | EMEA |

The underlying data is identical. Display names and format specs do the rest.

## The Structural Value

The most significant benefit is cross-team consistency. When Finance queries "net retention" and Product queries "expansion revenue", synonyms ensure both resolve to their respective correct columns — not because the model inferred correctly, but because **the definition is authoritative**.

Agent Metadata elevates the [[Semantic Layer]] from a BI presentation concern to a governed component of the data catalog: defined once in [[Unity Catalog]], version-controlled, subject to access policies, consumed automatically by every downstream tool.

## Related

- [[Unity Catalog]] — governance layer where Agent Metadata lives
- [[Metric Views]] — the construct Agent Metadata is attached to
- [[Semantic Layer]] — the broader architecture Agent Metadata contributes to
- [[Genie Agents]] — primary AI consumer
- [[Disambiguation]] — the core problem Agent Metadata solves
- [[Genie Ontology]] — structural complement: explicit synonym mappings vs. the ontology's dynamic, usage-based resolution
- [[Knowledge Store]] — the space-level complement: Agent Metadata is governed globally in Unity Catalog, the Knowledge Store is scoped per space
- [[Data Governance]] — Agent Metadata is the metadata-governance layer that makes AI consumption of data trustworthy
