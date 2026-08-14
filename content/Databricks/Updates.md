---
title: Updates
tags:
  - databricks
  - changelog
---

# Databricks GenAI — Update Log

Running log of confirmed developments surfaced by the daily briefing skill. Newest entries first.

## 2026-08-14

_No genuinely new items today. Checked the AI/BI and Genie One release notes page (still "Last updated Aug 6, 2026" — unchanged since the Aug 13 run, confirming nothing has posted since), the platform release notes, and the Databricks blog/general search for Genie, Mosaic AI, Unity Catalog, LakeFlow, Model Serving, Vector Search/AI Search, and MLflow. Everything surfaced (Kimi K3, DeepSeek V4 Flash, Pages, ABAC MCP/agent-service coverage, Lakeflow connectors, compliance-profile Lakebase) is already logged in prior entries. Also checked the "Databricks Grows >80% YoY, Surpasses $7B Revenue Run-Rate" press release (funding/valuation announcement, $5B round at $190B valuation) — financial/PR framing with no new GenAI product substance beyond already-logged Lakebase/Genie/Unity AI Gateway investment, left out per scope consistent with prior runs. Checked GitHub (databricks/databricks-agent-skills) and Reddit/community chatter — nothing new._

## 2026-08-13

_Checked the platform release notes page (now shows entries through Aug 13, vs. "Last updated Jul 31" on prior runs — the page itself had gone stale until now), AI/BI release notes (still no items past Aug 6), Databricks blog, and general Genie/Mosaic AI/LakeFlow/Agent Bricks searches. Several genuine deltas found in the Aug 10–13 backlog the platform release notes page had been silently sitting on._

**Ask Your Data / Genie / AI-BI**
- **Define business concepts with Pages** (Beta, Aug 12) — a new Unity Catalog semantics construct for giving business terms, acronyms, and KPIs a single governed definition. Pages form the human-modeled layer of [[Genie Ontology]] alongside Glossary and Domains — Genie One draws on them directly to ground its answers. Updates [[Genie Ontology]]. [Source](https://docs.databricks.com/aws/en/uc-semantics/pages)
- **Alert system tables** (Public Preview, Aug 10) — `system.alert.alerts` and `system.alert.alert_evaluation_history` let admins audit alert configuration and evaluation history at scale for AI/BI dashboard alerts. Minor, noted here rather than on a concept note. [Source](https://docs.databricks.com/aws/en/admin/system-tables/alerts)

**Unity Catalog / Governance**
- **ABAC GRANT policies extended to MCP services, agent services, and skills** (Beta, Aug 11) — previously scoped to models only, dynamic attribute-based GRANT policies now also cover model services, model provider services, MCP services, agent services, and skills — closing a real gap for governing the AI-agent surface specifically, not just data assets. Updates [[Unity Catalog]]. [Source](https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/grant-policies)
- **Tag automations** (Beta, Aug 7, backfilled — missed in prior runs) — rules that auto-assign or remove governed tags on Unity Catalog tables/volumes matching defined conditions (certify trusted data, deprecate stale data, roll up sensitivity tiers). Notably, automations can be authored **by describing the rule to Genie in natural language**, not just via a form — a small but real extension of NL interfaces into the governance layer itself. Updates [[Unity Catalog]]. [Source](https://docs.databricks.com/aws/en/admin/governed-tags/automate-tag-assignment)

**[[LakeFlow]]**
- **Gmail connector** (Beta, Aug 13), **Google Search Console connector** (Beta, Aug 12), **Notion connector** (Beta, Aug 10), and **NetSuite connector** (GA, Aug 4, backfilled — missed in prior runs) all added to Lakeflow Connect. Continues the pattern of governed ingestion from productivity/SaaS tools that then become queryable via Genie. Updates [[LakeFlow]]. [Sources: Gmail](https://docs.databricks.com/aws/en/ingestion/lakeflow-connect/gmail) · [Google Search Console](https://docs.databricks.com/aws/en/ingestion/lakeflow-connect/google-search-console) · [Notion](https://docs.databricks.com/aws/en/ingestion/lakeflow-connect/notion) · [NetSuite](https://docs.databricks.com/aws/en/ingestion/lakeflow-connect/netsuite)

**Model Serving / Foundation Model APIs**
- **DeepSeek V4 Flash (0731)** now available as a Databricks-hosted model (Aug 10, `us-west-2`) — 284B-parameter MoE model (13B active), optimized for fast/cheap reasoning, coding, and agentic tool use, via Foundation Model APIs. [Source](https://docs.databricks.com/aws/en/machine-learning/foundation-model-apis/supported-models#deepseek-v4-flash-0731)

**Mosaic AI / Agent Framework / [[Lakebase]]**
- **Lakebase now supports the compliance security profile** (HIPAA, C5, or TISAX controls, or compliance profile with no standard selected) by default (Aug 5, backfilled — missed in prior runs) — removes a real deployment blocker for using Lakebase-backed agent memory in regulated environments. Updates [[Lakebase]]. [Source](https://docs.databricks.com/aws/en/oltp/projects/data-protection)

_Note: checked "Databricks Elevates AI Agent Performance with Advanced Evaluation Tools" (Agent-as-a-Judge / Tunable Judges / Judge Builder) circulating in current search results — verified this actually shipped November 2025, predating this vault's coverage window; not a delta, dropped. Also checked the Aug 12 Databricks blog post "The Future of Data Analytics: Why AI is rewriting the Analyst's Job Description" — an opinion/positioning piece referencing already-logged capabilities (AI/BI Dashboards, Genie One, Genie Code), no new product substance, skipped as commentary rather than news. Checked GitHub (databricks-solutions, databrickslabs) — genie-code-skills-demo and databricks-genie-workbench repos show recent activity but no new capability beyond what's already logged. Databricks joining the "Open Secure AI Alliance" and the Panther acquisition completion were both judged out of scope (security/PR moves with no GenAI/Ask Your Data product angle), consistent with prior runs' treatment of similar items._

## 2026-08-12 (second run)

_Delta-only, checked against the same-day entry below. Re-checked the AI/BI release notes page (still "Last updated Aug 6, 2026" — confirmed unchanged), platform release notes (still no items past Aug 11's ABAC Grant expansion / READ METADATA GA, both left out per scope), and Databricks blog/general search for Genie Ontology, Agent Bricks, Unity Catalog, AI Search, and LakeFlow. Nothing new since the first run today — the Electric/PGlite item below already captured the one live thread._

## 2026-08-12

_Delta-only. Checked the AI/BI release notes page, platform release notes (Aug 10–11 entries were ABAC Grant policy expansion and Unity Catalog READ METADATA GA — generic governance items with no AI-specific angle, left out per scope), and Databricks blog for the Aug 11–12 window. One genuine delta found._

**Mosaic AI / Agent Framework / [[Lakebase]]**
- **Electric (maker of PGlite) joins Databricks to bring WASM Postgres to AI agent sandboxes** (Aug 11) — Electric's PGlite, a WASM-compiled build of Postgres with 13M weekly downloads, gives each individual agent sandbox its own local, ultra-low-latency Postgres instance; Electric's real-time sync engine keeps that distributed per-agent state synchronized back to a central [[Lakebase]] instance, so teams of agents can share context without losing consistency. Extends Lakebase's reach from "one serverless Postgres endpoint" to "edge Postgres in every agent sandbox + centralized sync." Updates [[Lakebase]]. [Source](https://www.databricks.com/blog/electric-joins-databricks-bring-wasm-postgres-ai-agent-sandboxes)

## 2026-08-11

_Delta-only. Checked the AI/BI and Genie One release notes page (docs.databricks.com/aws/en/ai-bi/release-notes/2026, "Last updated Aug 6, 2026" — unchanged since the last run, confirming nothing has posted since) against the vault log in full and found three genuinely new items from the Aug 6 dated section that prior runs missed. Also checked platform release notes, Databricks blog, and general Genie/Mosaic AI/LakeFlow searches for the Aug 10–11 window — nothing new posted since the second run on Aug 10._

**Ask Your Data / Genie / AI-BI**
- **Genie Ontology enabled by default** (Public Preview, Aug 6) — previously opt-in, the org-wide context layer now applies automatically to Genie One conversations without admin configuration. Updates [[Genie Ontology]]. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)
- **Upload PDF files to a Genie One conversation** (Beta, Aug 6) — PDFs can now be attached alongside CSV/Excel files; Genie One parses them asynchronously. Updates [[Genie One]]. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)
- **Markdown tables in Genie Agents Agent mode APIs** (Beta, Aug 6) — table visualizations in the Agent mode API response now return as markdown instead of table-visualization attachments, improving readability for API consumers. Updates [[Genie Agents]]. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

_Note: other Aug 6 dashboard items (rich text in widget titles, hide pivot table column headers, schedule run history) are generic dashboard UI polish without a GenAI/Ask Your Data angle and were left out per scope, as were bug fixes. Checked GitHub (databricks/databrickslabs) and community/Reddit chatter — nothing new._

## 2026-08-10 (second run)

**GenAI Engineering / [[Evaluation]]**
- **OfficeQA Pro V2 benchmark** (Aug 6) — a follow-up to Databricks' OfficeQA benchmark, built from ~1,400 U.S. Treasury PDFs (~120K pages) via a synthetic data pipeline, testing whether grounded-reasoning gains generalize beyond the original corpus. Out-of-the-box agents averaged only 26.0% accuracy; Genie delivered a 92% relative improvement over matched baseline models, reaching up to 60% accuracy. Updates [[Evaluation]]. [Source](https://www.databricks.com/blog/introducing-officeqa-pro-v2-new-benchmark-enterprise-grounded-reasoning)

_Note: also checked the Genie Code "Import BI files" docs page (last updated Jul 30) describing Tableau/Power BI import into AI/BI dashboards with local metric views — judged to be elaboration on the already-logged Aug 4 entry ("AI/BI dashboards can now import Power BI and Tableau reports directly") rather than a distinct new capability, so not re-logged. Checked platform/AI-BI release notes, Databricks blog, LakeFlow/Unity Catalog/Vector Search/Genie Ontology coverage — Panther acquisition (Aug 3, completed) is a security-lakehouse story with no GenAI/Ask Your Data angle and was left out per scope. Nothing else new since the first run today._

## 2026-08-10

_No genuinely new items today. Checked the full August 2026 platform release notes page (docs.databricks.com/aws/en/release-notes/product/2026/august, all entries dated Aug 3–7) against the vault log — every dated item on it (`ai_search` function, MCP connectors under Unity AI Gateway, Kimi K3, Genie Code web search, Genie One in Google Sheets/Excel, Unity AI Gateway GA, Full page Genie Code GA, SharePoint/Google Drive/PagerDuty connectors, etc.) is already logged in prior entries below. Also checked the AI/BI release notes page, Databricks blog, and general Genie/Mosaic AI/LakeFlow searches — no items dated Aug 8–10 surfaced. The page's own "Last updated" stamp (Jul 31) suggests nothing has posted since the Aug 9 run's coverage of the Aug 6–7 backlog._

## 2026-08-09

**Vector Search / [[AI Search]]**
- **`ai_search` SQL function** (Beta, Aug 7) — a new SQL function that takes a natural-language query plus up to 10 AI Search indexes as knowledge sources, generates optimized search queries, retrieves/dedupes/reranks results across sources, and by default synthesizes a grounded natural-language answer over the retrieved documents — all in one function call. Complements the existing `ai_prep_search` (chunking) function: `ai_parse_document` → `ai_prep_search` → index → `ai_search` now covers the full batch RAG pipeline in SQL. Updates [[AI Search]]. [Source](https://docs.databricks.com/aws/en/sql/language-manual/functions/ai_search)

**Model Serving / Foundation Model APIs**
- **Kimi K3 (Moonshot AI) now available** (Aug 6) — a 2.8T-parameter open-weight model with a 1M-token context window and native multimodal support, hosted by Databricks via Foundation Model APIs with full Unity AI Gateway governance and zero data retention. Databricks benchmarks it at parity with leading proprietary models (Anthropic, OpenAI, Gemini) at 50–72% lower cost-per-task. US-hosted initially (native on AWS/GCP, ADI access on Azure). [Source](https://www.databricks.com/blog/kimi-k3-moonshot-ai-now-available-databricks-through-unity-ai-gateway)

_Note: checked official release notes (platform, AI/BI), Databricks blog, MLflow/Agent Bricks/Lakebase coverage, GitHub (databricks/databrickslabs), and community/Reddit for the Aug 8–9 window. Both items above actually shipped Aug 6–7 but were missed by the Aug 8 run (which only covered the Genie One MCP server backfill) — logged now as a delta. No items dated Aug 8–9 itself cleared the confirmed-and-new bar; other August releases in this window (tag automations, materialized view change data feed, JAR tasks on serverless, REPLACE USING flows, Secrets in Unity Catalog) are generic platform/governance features without a GenAI/Ask Your Data angle and were left out per scope._

## 2026-08-08

**Ask Your Data / Genie / AI-BI** (backfilled — missed in prior runs)
- **Genie One MCP server** (Beta, docs last updated Aug 3) — a new Databricks-managed MCP server (`/api/2.0/mcp/genie`) that exposes [[Genie One]] itself as a conversational tool over MCP: any external MCP client or agent (Cursor, Claude Desktop, a custom orchestrator) can send a natural-language data question and get an answer grounded in Genie Ontology with source citations, with Unity Catalog permissions enforced throughout. Clients supporting MCP Apps get an interactive inline View (charts, progress, citations) instead of plain text. Distinct from the existing per-agent Genie MCP server (`/api/2.0/mcp/genie/{genie_space_id}`) and from the Aug 6 entry below about existing managed connectors moving under Unity AI Gateway — this is Genie itself becoming callable by outside agents, not Genie calling out. Requires the Managed MCP Servers workspace preview. Updates [[Genie One]] and [[MCP]]. [Source](https://docs.databricks.com/aws/en/agents/mcp-tools/genie-mcp)

_Note: checked official release notes (platform, AI/BI), Databricks blog, GitHub (databricks/databrickslabs), and community/Reddit chatter for the Aug 7–8 window — no other genuinely new items surfaced. A Gemini 3 Pro/Flash listing appeared in one aggregated search snippet but with internally inconsistent dates (a March 2026 retirement notice attached to it), suggesting stale/low-quality source content rather than a new addition since the last run — dropped per the confirmed-only filter._

## 2026-08-07

**Unity Catalog / Governance**
- **Databricks-managed MCP connectors now integrated with Unity AI Gateway** (Beta, Aug 6) — all Databricks-managed MCP connectors for [[Genie One]] and [[Genie Code]] have migrated under Unity AI Gateway, bringing centralized governance, access controls, and visibility alongside other MCP servers and tools. Existing users must reauthenticate affected connectors. Updates [[Unity Catalog]]. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

**Ask Your Data / Genie / AI-BI**
- **Genie Code web search** (Beta, Aug 6) — Genie Code can now search the public web to answer questions needing current information and cites its sources. Disabled by default; a workspace admin turns it on from the Previews page. Requires the Americas/Europe geo (or cross-geography processing enabled); under the compliance security profile, only HIPAA workspaces support it. Updates [[Genie Code]]. [Source](https://docs.databricks.com/aws/en/genie-code/use-genie-code#web-search)

**[[MLflow]] / GenAI Observability** (minor, upcoming)
- **MLflow 3 trace storage in Unity Catalog becomes the default** — for workspaces with the compliance security profile enabled, rolling out mid-August 2026 (previously a recommendation, not yet the default). Updates [[MLflow]]. [Source](https://docs.databricks.com/aws/en/release-notes/whats-coming)

## 2026-08-06

**Ask Your Data / Genie / AI-BI**
- **Genie One now available in Google Sheets and Microsoft Excel** (Aug 5) — via the Databricks Connector for Google Sheets and the Databricks Excel Add-in; query governed data in natural language and import results as native rows/columns. Updates [[Genie One]]. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

**Unity Catalog / Governance**
- **Unity AI Gateway Smart Routing** (Beta) — additional detail on the Aug 4 GA announcement not previously captured: dynamically routes each request to the model best suited by quality, cost, performance, availability, and budget, reserving expensive frontier models for tasks that need them. Updates [[Unity Catalog]]. [Source](https://www.databricks.com/blog/unity-ai-gateway-generally-available)

**[[LakeFlow]]** (backfilled — missed in prior runs)
- **OpenAI connector** (Beta, last updated Jul 31) and **Anthropic connector** (Beta, last updated Jul 17) in Lakeflow Connect — ingest each AI vendor's own organization admin/compliance data (users, projects, API keys, usage, costs, audit logs for OpenAI; audit logs, directory data, Claude chat/message data for Anthropic) into the governed lakehouse. Extends LakeFlow's SaaS-governance pattern to AI vendor spend itself. Updates [[LakeFlow]]. [Source](https://docs.databricks.com/aws/en/ingestion/lakeflow-connect/saas-overview)

**Vector Search / [[AI Search]]** (backfilled — missed in prior runs)
- **Dedicated full-text search index** (Beta, docs last updated Jul 20) — a Delta Sync Index with no embedding columns, for pure keyword/BM25 search on storage-optimized endpoints. Distinct from the hybrid vector+keyword search already available on standard indexes. Updates [[AI Search]]. [Source](https://docs.databricks.com/aws/en/ai-search/create-ai-search)

**Frameworks & Tools**
- **Agent Skills** — Databricks published its officially maintained `databricks/databricks-agent-skills` GitHub repo and a `databricks aitools` CLI command group, packaging Databricks-specific development knowledge as Agent Skills (open standard) for Claude Code, GitHub Copilot, and Cursor. Ties directly into full-page Genie Code's new personalization-via-skills capability. New note created: [[Agent Skills]]. [Source](https://docs.databricks.com/aws/en/agent-skills/)

**Semantic Layer / Metric Views** (minor)
- **Metric Views window measures now support a numeric index column** (Aug 5) — unitless numeric `offset` and `trailing`/`leading` ranges on a consecutive integer `order` column, for comparing along non-calendar business periods (e.g. fiscal weeks, 4-4-5 accounting periods). Not added to [[Metric Views]] note — too narrow a technical detail to warrant a dedicated line there. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

_Note: today's "Agents at Work: Shipping Agentic Apps at Scale" joint Databricks/OpenAI webinar (Aug 4 AMER / Aug 5 EMEA / Aug 6 APAC) was checked but didn't surface capabilities beyond what's already logged (org-wide policies, unified skill/MCP registry, permissions, auditability) — skipped as recap rather than new information._

## 2026-08-05 (second run)

_Delta-only — checked against the same-day entry below. Official Databricks sources (platform release notes, AI/BI release notes) showed no new dated items since the first run today._

**Ecosystem / Open Source**
- **OntoBricks** (databrickslabs, actively maintained — 199 stars, 458+ commits) — transforms Unity Catalog tables into a materialized, reasoned knowledge graph (OWL ontology design, R2RML mapping, Delta-backed triple store + Lakebase Postgres graph engine, OWL 2 RL/SWRL/SHACL reasoning), queryable via auto-generated GraphQL and an MCP server. Community project, not an official Databricks product. New note created: [[OntoBricks]]. [Source](https://github.com/databrickslabs/ontobricks)

## 2026-08-05

**Partnerships**
- **Microsoft and Databricks extended their strategic partnership into the 2030s** (announced July 23). Databricks is moving its own internal business operations onto Azure Databricks and adopting Azure Cobalt 200 (Arm-based infra, ~50% perf improvement). Genie, [[Genie Ontology]], and Unity AI Gateway are being integrated directly into Microsoft 365, Teams, Copilot, Power BI, and Purview. [Source](https://news.microsoft.com/source/2026/07/23/databricks-and-microsoft-expand-partnership-to-help-enterprises-bring-business-context-to-enterprise-ai/)

**Mosaic AI / Agent Framework**
- **[[Omnigent]] open-sourced** (Apache 2.0, June) — a new "meta-harness" category that sits above agent frameworks (Claude Code, Codex, Pi), letting teams compose, govern, and share agents from one layer. Enforces guardrails (cost budgets, permissions) statefully at the harness level rather than via prompts an agent could reason around; sandboxes filesystem/network access; supports live shared agent sessions. Databricks offers a fully managed version. See [[Omnigent]]. [Source](https://www.databricks.com/blog/introducing-omnigent-meta-harness-combine-control-and-share-your-agents)
- **[[Agent Bricks]] expanded framework support** — now builds on Claude Code SDK, [[LangGraph]], Agno, CrewAI, and OpenAI Agent SDK, with horizontal autoscaling via Databricks Apps. Databricks cites 100K+ agents built and 1+ quadrillion tokens/year processed on the platform. [Source](https://www.databricks.com/blog/agent-bricks-dais-2026)

**Ask Your Data / Genie / AI-BI**
- **Genie One**: chats can now be shared read-only account-wide; added connections to Gmail plus Teams/Outlook/Calendar in Microsoft 365; a Genie Agent can now read files sitting in Unity Catalog volumes (PDFs, slide decks, images) rather than only structured tables. Updates [[Genie One]].
- **Chart explain-in-place** — right-click a bar/line/area time-series visualization and ask Genie to explain a change; it enters Agent Mode to identify top drivers automatically. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

**Model Serving / Foundation Model APIs**
- **Gemini 2.5 Pro** (Google's hybrid reasoning model, "Deep Think" mode, built-in audio output) now available via Databricks Foundation Model APIs on pay-per-token pricing, alongside existing hosted models like Llama 3.3 70B. [Source](https://docs.databricks.com/aws/en/machine-learning/foundation-model-apis/supported-models)

**[[MLflow]] / GenAI [[Observability]]**
- **MLflow 3 tracing** now runs on a production-scale trace-ingestion backend for real-time observability. Databricks now recommends storing traces in Unity Catalog for new/production workloads — queryable via SQL like any Delta table, governed the same way. Automatic instrumentation spans 20+ frameworks. Updates [[MLflow]]. [Source](https://docs.databricks.com/aws/en/mlflow3/genai/tracing/)

**Vector Search / [[AI Search]]** (backfilled from DAIS 2026 — missed in the first run)
- **Lakebase Search announced** (June 16) — hybrid vector + full-text retrieval built directly into Lakebase Postgres via two new extensions, `lakebase_vector` (pgvector-compatible ANN search, ~32x index compression via RaBitQ, scales past 1B vectors) and `lakebase_text` (BM25 full-text without GIN's RAM bloat). Beta on AWS and Azure. Distinct from the already-noted Vector Search → AI Search rebrand: AI Search is the fully managed option, Lakebase Search is the Postgres-native one for agent memory/retrieval on a single backend. New note created: [[Lakebase Search]]. Also created [[AI Search]] to formally cover the rebrand flagged in the 2026-08-04 entry below. [Source](https://www.databricks.com/blog/announcing-lakebase-search-agent-native-retrieval-built-lakebase-postgres)

**Unity Catalog / Governance**
- **Unity AI Gateway is now formally GA** (August 4 release notes) — was announced/previewed at DAIS 2026 (see below); service policies and agent services remain in Beta. Updates [[Unity Catalog]]. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

**Ask Your Data / Genie / AI-BI**
- **Full page Genie Code is now GA** (August 4) — command-center layout: active chat prominent, notebooks/files open as tabs alongside it, multiple parallel chats, personalization via skills/instructions/MCP servers. Updates [[Genie Code]]. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

**[[LakeFlow]]**
- **SharePoint connector now GA** and **Google Drive connector now GA** in Lakeflow Connect (August 4). **PagerDuty connector** now in Beta — ingests incident, on-call, service, and audit data. [Source](https://docs.databricks.com/aws/en/release-notes/product/2026/august)

## 2026-08-04

_First run for this project — no prior baseline, so this entry is broader than a typical daily delta._

**Ask Your Data / Genie / AI-BI**
- **Genie One + Genie Agents free usage extended to January 31, 2027** (previously ended July 31, 2026). Service principal usage is still billed; budget controls don't apply during the promo. Updates the pricing note in [[Genie Agents]]. [Source](https://learn.microsoft.com/en-us/azure/databricks/genie/monitor-cost)
- **[[Genie Ontology]]** — a continuously learned enterprise context layer, built on Unity Catalog Glossary/Domains, now feeds Genie so it understands business concepts without per-agent configuration. Announced at DAIS 2026. [Source](https://www.databricks.com/blog/introducing-genie-one-genie-ontology-and-genie-agents)
- **[[Genie One]]: Ontology snippets** now in Public Preview. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)
- AI/BI dashboards can now **import Power BI and Tableau reports directly** as a new dashboard from the dashboard list page. [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

**Mosaic AI / Agent Framework**
- **[[Agent Bricks]] Supervisor Agent is now GA** — orchestrates multiple enterprise agents. [Source](https://www.databricks.com/blog/agent-bricks-supervisor-agent-now-ga-orchestrate-enterprise-agents)
- **[[Agent Bricks]] Document Intelligence is now GA** — SQL functions `ai_parse_document`, `ai_extract`, `ai_classify` for document parsing/analysis at scale. [Source](https://www.databricks.com/blog/agent-bricks-dais-2026)
- **Managed memory for agents**, powered by [[Lakebase]] — agents can persist context and session history across sessions without custom infrastructure. [Source](https://www.databricks.com/blog/agent-bricks-dais-2026)

**Unity Catalog / Governance** (see also [[Unity Catalog]])
- **Unity AI Gateway** — new runtime governance layer for models, agents, tools, and MCP connections. **Contextual Service Policies** (now Beta) let admins allow/deny/require-approval for specific agent actions (e.g. writing to sensitive folders). AI Gateway budgets now also cover external, bring-your-own-key providers. [Source](https://www.databricks.com/blog/whats-new-unity-catalog-data-ai-summit-2026)
- **ABAC Grant Policies** in Beta for models — define attribute-based access once, auto-grant EXECUTE across matching models. Identity Attributes and Context Attributes coming soon in preview.
- **Glossary** (coming soon) and **Domains** (Public Preview) — shared, governed business terminology and business-aligned data organization, both feeding [[Genie Ontology]].
- **External Lineage now GA** — extends Unity Catalog lineage to non-Databricks source/downstream systems; Lakeflow Connect pipelines auto-record source lineage. Updates [[Data Lineage]]. [Source](https://docs.databricks.com/aws/en/data-governance/unity-catalog/external-lineage)
- **Cross-cloud, cross-region addressability** — new four-level namespace (`metastore.catalog.schema.table`) gives every asset one address across a whole Databricks footprint.
- **Metrics** (formerly Metric Views) significantly expanded: multi-fact relationships (Public Preview in Dashboards), level-of-detail calculations, parameterized metrics, query Materialization (Public Preview), and import from Power BI/Tableau (Beta). Updates [[Metric Views]].

**Vector Search / [[AI Search]]**
- **Databricks Vector Search has been rebranded to "[[AI Search]]"** (Python SDK now `databricks-ai-search`). See [[AI Search]].
- **Storage Optimized [[AI Search]] endpoints** — new deployment option for billion-scale vector indexes, decoupling storage (cloud object storage) from compute. Builds billion-vector indexes in under 8 hours (20x faster than Standard), up to 7x lower serving cost, using a custom IVF + Product Quantization architecture with a Rust query engine. Trade-off: ~300–500ms query latency vs. 20–50ms on Standard endpoints. [Source](https://www.databricks.com/blog/decoupled-design-billion-scale-vector-search)
- **`ai_prep_search`** SQL function in Beta — transforms `ai_parse_document` output into search-ready chunks for [[RAG]] pipelines.
- Built-in **retrieval quality evaluation** for comparing search strategy relevance.

**[[LakeFlow]]**
- **Row filtering in Lakeflow Connect is now GA** — ingest only rows matching a condition, applied on both initial load and incremental updates; supported for Google Analytics, Salesforce, ServiceNow, and all query-based connectors.
- **Veeva Vault connector** in Beta (via Veeva's Direct Data API).
- **Integrated MySQL CDC pipeline** in Beta — combines extraction and application into a single pipeline.
- Simplified continuous pipeline/job configuration (schedule directly from the pipeline page) — announced for early August 2026, not yet confirmed live as of this run.

_Note: this first run surfaced an unusually large backlog since there's no prior baseline — expect future entries to be much shorter, delta-only updates._
