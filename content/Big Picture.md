---
title: Big Picture
tags:
  - synthesis
  - big-picture
  - changelog
---

# Big Picture — Cross-Cutting Synthesis Log

Running log of cross-cutting patterns and strategic reads across the ask-your-data knowledge base, generated daily by the `big-picture-daily` task (which runs shortly after `data-landscape-daily-digest`). Distinct from [[Databricks/Updates|Databricks Updates]] and [[Market Landscape/Updates|Market Landscape Updates]], which log individual dated findings — this log tracks the synthesis layer built on top of them: convergence, divergence, whitespace, escalation, contradiction, and consolidation patterns spanning multiple vendors and/or multiple days.

**How this doc is maintained:** each observation is logged once, under the date it was first identified, and revised in place on later runs rather than re-logged from scratch. Before writing anything, the daily run reads this doc in full and checks each new candidate pattern against the existing observations below:
- **New pattern, no match** → add a new observation.
- **Matches an existing observation, new supporting evidence** → append a dated line under that observation's "Update log" and extend the "Built on" citations; only rewrite the synthesis prose if the new evidence changes the actual take, not just to restate it.
- **Matches an existing observation, materially changes or reverses the take** → rewrite the synthesis prose, note what changed and why in the update log, and bump "Last updated."
- **Nothing new anywhere** → no doc edit; just add a one-line entry to the Quiet Days log at the bottom so the record shows the day was checked.
- An observation that's been fully overtaken by events (rare) moves to Retired/Superseded rather than being deleted, with a one-line note on what superseded it.

---

## Active Observations

### Chat is becoming an app-builder
**First logged:** 2026-09-08 · **Last updated:** 2026-09-13 · **Status:** active — escalation

Every major platform in this space now offers some path from "ask a question" to "here's a live internal tool," not just a chat answer. Amazon's Quick Apps reached GA Sep 1 — full natural-language-built internal tools, live-connected to source systems — landing alongside [[Market Landscape/TextQL|TextQL]]'s Data Apps (Git-native, warehouse-write-back), [[Sigma]]'s Workbooks-as-Code, and Databricks' own [[Genie App Builder]]. Omni is now a fifth data point: its generative "Apps" feature (build an interactive app from a prompt) reached GA the week of Aug 31 and is on by default in embedded instances — a smaller vendor than the other four, but the same bet. This is the category maturing past Q&A; the next competitive fight is over app-authoring UX and governance, not answer accuracy.

**Built on:**
- Amazon Quick Apps reaches GA (Sep 1) — [Source](https://aws.amazon.com/about-aws/whats-new/2026/09/amazon-quick-custom-apps-natural-language/)
- TextQL Data Apps, launched Jul 30 (backfilled into the vault Sep 1) — [Source](https://textql.com/blog/data-apps-launch)
- Sigma Workbooks-as-Code and Databricks Genie App Builder (existing vault coverage, referenced for comparison)
- Omni Apps reaches GA, on by default in embedded instances (week of Aug 31, logged Sep 12) — [Source](https://docs.omni.co/changelog)

**Update log:**
- 2026-09-08: initial observation.
- 2026-09-13: added Omni Apps GA as a fifth confirming vendor — the pattern is now a checklist item across the category, not a handful of vendors' individual bets.

---

### MCP as the universal semantic-layer exit door
**First logged:** 2026-09-08 · **Last updated:** 2026-09-13 · **Status:** active — standards/consolidation

[[MCP]] isn't just a connectivity protocol anymore — it's becoming the default way vendors expose (and govern) their semantic/context layer to any agent. Microsoft's Fabric IQ Ontology got an MCP server (Preview, Aug 29), explicitly following "the same pattern already seen from Databricks and Snowflake" per the market-landscape log itself — Databricks' Genie One MCP server, Snowflake's Cortex Agents/MCP Native Apps, and [[Market Landscape/Strategy|Strategy]] Mosaic's own MCP server all do the same thing. On the Databricks side, Unity Gateway's unified trace table (Beta, Sep 1) went a step further and turned every MCP tool call itself into a governed, queryable artifact — Databricks used it internally to catch $499K/year in wasted agent spend. This window sharpens the pattern in two directions at once. Vendors are formalizing their own MCP exposure into discoverable, productized channels rather than leaving it as a generic capability: Sigma shipped a dedicated, officially-listed ChatGPT plugin (Sep 11) that's explicitly a productized front-end on the same MCP server it already had, and Omni added MCP tools for downloading dashboards programmatically (logged Sep 12). And the traffic is now running the other way too: Databricks' first-party managed MCP connector catalog (Google Drive, Gmail, Calendar, Microsoft 365, Atlassian, Slack, GitHub) reached GA for Genie One and Genie Code (Sep 10), governed end-to-end through Unity Catalog/Gateway — so MCP isn't just how a vendor's semantic layer gets consumed by outside agents anymore, it's also becoming the default way a vendor's own agent reaches into everyone else's tools. It's turning into two-way integration fabric for the whole category, not a one-directional "exit door." Worth watching whether this tips into an actual cross-vendor MCP interop spec, not just parallel implementations in both directions.

**Built on:**
- Fabric IQ Ontology MCP reaches Preview (Aug 29) — [Source](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-fabric-iq-ontology)
- Unity Gateway unified trace table reaches Beta (Sep 1) — [Source](https://www.databricks.com/blog/how-we-eliminated-1-million-year-wasted-ai-agent-spend-one-hour)
- Strategy Mosaic's own MCP server (existing vault coverage, backfilled Aug 30) — [Source](https://software.strategy.com/strategyai/agents)
- Sigma plugin for ChatGPT, productizing its existing MCP server (Sep 11) — [Source](https://help.sigmacomputing.com/docs/use-the-sigma-plugin-for-ai-assistants)
- Databricks-provided MCP connectors for Genie One/Genie Code reach GA (Sep 10) — [Source](https://docs.databricks.com/aws/en/genie-one/external-sources)
- Omni MCP dashboard-download tools (week of Aug 31, logged Sep 12) — [Source](https://docs.omni.co/changelog)

**Update log:**
- 2026-09-08: initial observation.
- 2026-09-13: added evidence MCP is now bidirectional infrastructure — vendors productizing their own exposure (Sigma's ChatGPT plugin, Omni's dashboard tools) while also consuming third-party tools through it (Databricks' managed connector catalog GA); take sharpened from "exit door" to "two-way fabric."

---

### Semantic-layer portability tension: platform-native vs. customer-owned
**First logged:** 2026-09-08 · **Last updated:** 2026-09-08 · **Status:** active — diverging bets

Databricks extending [[Metric Views]] sharing cross-account/cross-metastore via OpenSharing (Beta, Sep 3) is a tacit concession to the pitch [[Market Landscape/Strategy|Strategy]] Mosaic and [[Market Landscape/TextQL|TextQL]]'s Ontology have been making all along: a semantic layer shouldn't be locked to one warehouse. Mosaic connects to 200+ sources without moving data and serves any BI tool or agent via SQL/DAX/MDX/MCP; TextQL's Ontology is Git-native and customer-owned outright. Databricks stretching sharing *within* its own governance boundary versus Strategy/TextQL being warehouse-agnostic from day one is the same problem solved from opposite starting points — a good tell for how defensible "platform-native" semantic layers really are long-term, and a candidate framing for a future article.

**Built on:**
- Metric views shareable via OpenSharing, Beta (Sep 3) — [Source](https://docs.databricks.com/aws/en/opensharing/create-share#metric-views)
- Strategy Mosaic — standalone universal semantic layer, 200+ sources (existing vault coverage, backfilled Aug 30) — [Source](https://software.strategy.com/strategymosaic)
- TextQL Ontology — Git-native, customer-owned (existing vault coverage)

**Update log:**
- 2026-09-08: initial observation.

---

### Agent memory becoming table stakes
**First logged:** 2026-09-08 · **Last updated:** 2026-09-13 · **Status:** active — converging moves, now confirmed

Three independent vendors have now shipped near-identical persistent-memory UX within about eight weeks of each other: [[Genie One]] Memory (Beta, shipped Jul 16), Strategy AI Agents' Long-Term Memory (shipped Aug 14), and — the confirming signal this observation flagged on Sep 8 as worth watching for — ThoughtSpot's Spotter Memory reaching **GA, on by default** (Sep 9). All three land on the same design: user-reviewable, correctable, cited when used. ThoughtSpot went further than a same-shape catch-up: Spotter Memory can now be generated directly from Liveboards (not just conversation turns), and a new "Remember this" button shows a preview of the exact definition being stored before the user commits — arguably a cleaner trust/consent pattern than either Genie One's or Strategy's current implementation. With three unrelated vendors converging on the same feature within two months, this has moved past "signal to watch" — persistent memory is now a baseline expectation for any serious NL-BI agent, not a differentiator. Genie One has since closed the specific consent gap this observation flagged: **Memory confirmation prompts (Beta, Sep 10)** now have Genie One proactively suggest a memory and require the user to approve, modify, or reject it before saving, rather than only saving on explicit request — converging on the same preview-before-commit shape ThoughtSpot introduced. That's a second-order signal worth noting on its own: not just "has memory" converging, but the *consent UX around* memory converging too. Sigma and Fabric IQ are the two notable vendors in this vault's coverage with no shipped memory feature yet — worth checking whether they follow, and whether being last matters competitively once a capability is this normalized.

**Built on:**
- Genie One Memory, Beta, shipped Jul 16 (backfilled Sep 2) — [Source](https://docs.databricks.com/aws/en/genie-one/chat#add-to-genie-ones-memory)
- Strategy AI Agents Long-Term Memory, Aug 14 release — [Source](https://software.strategy.com/blog/august-2026-agents-that-remember-mosaic-schema-in-studio-and-personalized-bi)
- ThoughtSpot Spotter Memory reaches GA, on by default (Sep 9) — [Source](https://docs.thoughtspot.com/cloud/26.9.0.cl/notes.html)
- Genie One Memory confirmation prompts, Beta (Sep 10, logged Sep 12) — [Source](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)

**Update log:**
- 2026-09-08: initial observation (two vendors, flagged as pattern to watch).
- 2026-09-09: reworked — ThoughtSpot Spotter Memory GA is the third independent vendor, confirming the pattern as settled table stakes rather than an emerging trend; take changed from "watch for a confirming signal" to "confirmed, Sigma/Fabric IQ now the outliers."
- 2026-09-13: added Genie One's Memory confirmation prompts (Beta, Sep 10) — directly closes the consent-UX gap this observation noted on Sep 9, and reframes the pattern one level up: the approve-before-save interaction is now also converging, not just the underlying memory capability.

---

### Adaptive execution tiering: quality-latency tradeoffs move into the engine
**First logged:** 2026-09-10 · **Last updated:** 2026-09-10 · **Status:** active — converging moves

Two vendors shipped the same underlying idea on the same day: instead of running every query through a fixed-cost pipeline, let the engine decide per-query how much work is worth doing. Databricks' new Adaptive Instructed-Retriever (Sep 9) — the retrieval model now sitting under Genie Code, Genie One, and Genie Agents — decides per-query how many search steps to take, stopping early on simple lookups and going deeper on hard multi-hop questions, cutting latency roughly 2x at matched quality against Claude Sonnet 5, GPT-5.6 Luna, and DeepSeek-V4-Flash. The same day, ThoughtSpot's 26.9.0.cl release took aggregate-aware query execution to GA — Spotter now auto-switches between detailed and aggregate semantic models based on query granularity for the same cost/latency payoff. Different subsystems (retrieval vs. semantic-model routing), same strategic move: once basic NL-to-answer works, the next differentiation axis is making the "how hard should I try" decision invisible and automatic rather than a knob someone has to tune. Worth watching whether this becomes a checkbox feature the way memory did, or stays a genuine performance differentiator.

**Built on:**
- Adaptive Instructed-Retriever (Sep 9) — [Source](https://www.databricks.com/blog/adaptive-instructed-retriever-frontier-quality-search-2x-lower-latency)
- ThoughtSpot 26.9.0.cl, aggregate-aware query execution reaches GA (Sep 9) — [Source](https://docs.thoughtspot.com/cloud/26.9.0.cl/notes.html)

**Update log:**
- 2026-09-10: initial observation.

---

### Lakebase branching becomes the substrate for agent-dev tooling
**First logged:** 2026-09-10 · **Last updated:** 2026-09-10 · **Status:** active — whitespace/consolidation (caveat: single-vendor signal)

Two independent Databricks field-engineering reference projects, two days apart, both reached for the same underlying primitive — Lakebase's copy-on-write Postgres branching — to solve completely different agent-tooling problems. Temporal + Lakebase (Sep 8) uses a branch as the durable, queryable, application-facing state store for long-running agent workflows that Temporal's own Event History doesn't expose well. Consort (Sep 9) uses a branch as a live, disposable test target for an agentic TDD loop, so a coding agent tests against real data shape instead of mocks. Neither is a core, SLA-backed product — both are open-source reference implementations from Field Engineering — so this is a signal about where Databricks' own engineers see the platform's edge, not a shipped capability. But it suggests Lakebase branching is quietly becoming a general-purpose "give an agent a safe, disposable copy of reality" primitive, distinct from Lakebase's original serverless-Postgres-for-agent-memory framing. Worth watching whether this surfaces as an official product feature, and whether any competitor's database offers something comparable for agent tooling specifically.

**Built on:**
- Temporal + Lakebase durable agents reference implementation (Sep 8) — [Source](https://www.databricks.com/blog/build-durable-agents-temporal-and-lakebase)
- Consort: open-source agentic TDD framework on Lakebase branching (Sep 9) — [Source](https://www.databricks.com/blog/introducing-consort-test-driven-development-branching-database)

**Update log:**
- 2026-09-10: initial observation.

---

### Citations become the default trust layer — but they don't prove anything
**First logged:** 2026-09-11 · **Last updated:** 2026-09-11 · **Status:** active — converging moves

Three vendors shipped answer-attribution features within a two-day window. Databricks' `ai_search` function got a `generate_citations` option (Beta, Sep 8) that returns which retrieved chunks the model used to support an answer. Amazon Quick's Sep 9 release added inline citations letting users "verify every answer against its source." ThoughtSpot's 26.9.0.cl (also Sep 9) shipped a quick action to "verify reasoning" on any Spotter answer. Add Genie One's existing citation behavior (web search results, Sep 1; memory, cited when used) and this isn't three isolated features — it's the market converging on "show your sources" as the standard answer to the trust problem, the same way memory converged a few weeks ago. The catch, and it's a real one: this vault's own [[Hallucinations]] note already classifies fabricated citations as a distinct failure mode ("invents plausible-sounding... citations that don't exist"), and Databricks' own release notes for `generate_citations` admit the citations are "the model's best-effort picks of supporting evidence, not proof of any specific claim." So the entire industry is racing to ship a trust UI built on exactly the mechanism most likely to be silently wrong. Worth a skeptical angle for a future piece — citations reduce blind trust in prose answers, but they're a UX signal of confidence, not a correctness guarantee, and nothing here changes that.

**Built on:**
- Databricks `ai_search` `generate_citations` option, Beta (Sep 8) — [Source](https://docs.databricks.com/aws/en/sql/language-manual/functions/ai_search)
- Amazon Quick inline citations, part of the Sep 9 always-on/enterprise-controls release — [Source](https://aws.amazon.com/about-aws/whats-new/2026/09/amazon-quick-always-on-agents-sharper-feed-enterprise-controls/)
- ThoughtSpot 26.9.0.cl, "verify-reasoning" quick action on Spotter answers (Sep 9) — [Source](https://docs.thoughtspot.com/cloud/26.9.0.cl/notes.html)
- Existing vault framing: [[Hallucinations]] (fabrication failure mode includes invented citations); Genie One web search citations (Sep 1) and memory citations (existing)

**Update log:**
- 2026-09-11: initial observation.

---

### NL-BI agents go always-on: background execution becomes the default
**First logged:** 2026-09-11 · **Last updated:** 2026-09-11 · **Status:** active — escalation

Three shipments across two vendors show agents shifting from "runs while you watch" to "runs whether or not you're there." Databricks took Genie Code scheduled tasks to GA (Sep 1) and added mobile push notifications so a Genie One scheduled task can complete and notify without an open session (Public Preview, Sep 3). Amazon went further on Sep 9: Quick's scheduled and monitoring agents now run in the cloud and keep delivering results "even when a user's laptop is closed," paired with a redesigned activity feed (daily briefings refreshing three times a day, a week of searchable history) built specifically to catch up on what agents did while unattended. Amazon also added a publishable agents/skills catalog — teams can share what they built rather than everyone reinventing it, echoing Genie One's own user-skills and shareable-Genie-Agent mechanisms. Read together, the center of gravity is moving from "chat interface you drive" to "fleet of agents you check in on" — the UI questions that matter next are less about query accuracy and more about surfacing what unattended agents did, flagging what needs a human, and making it easy to trust a summary you didn't watch get generated.

**Built on:**
- Genie Code scheduled tasks reach GA (Sep 1) — [Source](https://docs.databricks.com/aws/en/genie-code/scheduled-tasks)
- Genie One scheduled-task push notifications, Public Preview (Sep 3) — [Source](https://docs.databricks.com/aws/en/genie-one/mobile#push-notifications)
- Amazon Quick always-on cloud-persistent agents + redesigned activity feed (Sep 9) — [Source](https://aws.amazon.com/about-aws/whats-new/2026/09/amazon-quick-always-on-agents-sharper-feed-enterprise-controls/)

**Update log:**
- 2026-09-11: initial observation.

---

### "Deep research" becomes NL-BI's second tier, above single-turn Q&A
**First logged:** 2026-09-12 · **Last updated:** 2026-09-12 · **Status:** active — converging moves

Snowflake quietly established this months ago — CoWork's Deep Research reached GA back on Jul 7, turning "multi-step research report" into a shipped, governed output distinct from a chat answer. Google Cloud is now visibly converging on the same shape: its Jul 29 "multidimensional deep dive" (10–20 contributing factors analyzed in one run) has now hardened into a named **Deep Dive thinking mode** (Preview, dated Sep 3 but only caught by this vault's own tracking today — a week-plus miss worth noting on its own) that breaks a complex question into sub-questions, investigates each, and synthesizes a report — at the explicit cost of 3–5 minute queries and no multi-turn conversation during the solve phase. That's a real trade Google is choosing to make, not a free upgrade: it's carving out a second, slower, deliberately-more-thorough mode sitting above the fast single-turn chat answer, the same two-speed shape Snowflake already shipped. Databricks' Adaptive Instructed-Retriever (Sep 9) is a related but distinct move — it's about making the *existing* fast path adaptively cheaper, not adding a second, deliberately-slower investigative mode — so Databricks doesn't yet have an equivalent to Deep Research/Deep Dive. Worth watching whether Genie One or Genie Ontology ships one, and whether ThoughtSpot/Sigma/Fabric IQ follow the way they converged on memory a few weeks back.

**Built on:**
- Google Cloud Conversational Analytics API, Deep Dive thinking mode, Preview (dated Sep 3, surfaced in this vault Sep 11) — [Source](https://docs.cloud.google.com/gemini/data-agents/conversational-analytics-api/release-notes)
- Google Cloud Conversational Analytics API, "multidimensional deep dive" mode (Jul 29, existing vault backfill) — [Source](https://cloud.google.com/blog/products/data-analytics/conversational-analytics-in-google-data-cloud-in-q326)
- Snowflake CoWork Deep Research reaches GA (Jul 7, existing vault coverage) — [Source](https://docs.snowflake.com/en/release-notes/2026/other/2026-07-07-snowflake-cowork-deep-research-ga)
- Databricks Adaptive Instructed-Retriever, contrasted as a distinct efficiency-not-depth move (Sep 9, existing vault coverage) — [Source](https://www.databricks.com/blog/adaptive-instructed-retriever-frontier-quality-search-2x-lower-latency)

**Update log:**
- 2026-09-12: initial observation.

---

## Retired / Superseded Observations

_None yet._

---

## Quiet Days

_Dated log-only line for each run where no new pattern, and no update to an existing observation, was found — so the record shows the day was checked rather than skipped. No entries yet; this doc's first run (2026-09-08) had four active observations._
