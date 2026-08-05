---
title: RAG
aliases:
  - Retrieval-Augmented Generation
  - Retrieval Augmented Generation
type: "[[Concept]]"
context: GenAI
tags:
  - framework
  - ai-quality
---

## Definition

Retrieval-Augmented Generation (RAG) is a technique that enhances LLM responses by retrieving relevant documents from an external knowledge base before generating an answer. The model combines retrieved context with its parametric (training-time) knowledge, producing responses grounded in verifiable, organization-specific sources.

## How It Works

1. User query is converted to a vector embedding
2. The embedding is compared against an indexed knowledge base (vector store, BM25 index, or hybrid)
3. Top-K most relevant chunks are retrieved
4. Retrieved content is injected into the LLM's context alongside the query
5. LLM generates a response grounded in the retrieved content, with citations back to sources

## Why RAG Matters

Without retrieval, LLMs answer from training data, which is frozen at a cutoff date and knows nothing about organization-specific documents. RAG grounds responses in current, specific content without retraining the model.

Key benefits:
- **Source citations** — retrieved documents are citable, making answers verifiable
- **Reduced [[Hallucinations]]** — grounding in source text constrains fabrication
- **Domain specificity** — answers reflect organizational knowledge bases, policies, product docs
- **No retraining** — add new documents to the index; model stays the same

## RAG vs. Structured Data Querying

In data analytics, RAG and [[Natural Language to SQL]] address different data types:

| | RAG | NL-to-SQL |
|--|-----|-----------|
| Data type | Unstructured (documents, PDFs, emails) | Structured (tables, metrics) |
| Retrieval mechanism | Semantic similarity search | Schema mapping + SQL generation |
| Output | Natural language with citations | Table results + visualizations |

Both are often combined in multi-agent systems:
- [[Genie Agents]] handles structured SQL queries
- A RAG agent handles document retrieval
- A supervisor ([[Agent Bricks]], [[LangGraph]]) routes queries to the right agent

## Retrieval in Databricks

| Product | Best fit |
|---------|---------|
| **[[AI Search]]** | Fully managed — ingestion, embedding, reranking handled automatically |
| **[[Lakebase Search]]** | Postgres-native — retrieval alongside agent operational data in a single backend |

Document preparation for RAG pipelines: [[Agent Bricks]] Document Intelligence (`ai_parse_document` → `ai_prep_search`).

## RAG Variants

The field has produced several extensions to naive "retrieve then generate":

- **Self-RAG** — model decides whether retrieval is needed per query
- **Corrective RAG** — evaluates retrieved documents and retrieves more if quality is low
- **GraphRAG** — retrieves from a knowledge graph rather than a flat document index
- **Long RAG** — handles very long retrieved contexts

## Related

- [[AI Search]] — Databricks' managed retrieval layer for RAG pipelines
- [[Lakebase Search]] — Postgres-native hybrid search for agent-first workloads
- [[Agent Bricks]] — Document Intelligence prepares source documents for RAG indexing
- [[Hallucinations]] — the failure mode RAG reduces by grounding in source documents
- [[Genie Agents]] — combines with RAG agents in multi-agent systems
- [[LangGraph]] — orchestration framework for routing between RAG and SQL agents
- [[Evaluation]] — RAG pipelines require evaluation just like any GenAI system
