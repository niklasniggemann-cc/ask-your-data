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
**First logged:** 2026-09-08 · **Last updated:** 2026-09-08 · **Status:** active — escalation

Every major platform in this space now offers some path from "ask a question" to "here's a live internal tool," not just a chat answer. Amazon's Quick Apps reached GA Sep 1 — full natural-language-built internal tools, live-connected to source systems — landing alongside [[Market Landscape/TextQL|TextQL]]'s Data Apps (Git-native, warehouse-write-back), [[Sigma]]'s Workbooks-as-Code, and Databricks' own [[Genie App Builder]]. This is the category maturing past Q&A; the next competitive fight is over app-authoring UX and governance, not answer accuracy.

**Built on:**
- Amazon Quick Apps reaches GA (Sep 1) — [Source](https://aws.amazon.com/about-aws/whats-new/2026/09/amazon-quick-custom-apps-natural-language/)
- TextQL Data Apps, launched Jul 30 (backfilled into the vault Sep 1) — [Source](https://textql.com/blog/data-apps-launch)
- Sigma Workbooks-as-Code and Databricks Genie App Builder (existing vault coverage, referenced for comparison)

**Update log:**
- 2026-09-08: initial observation.

---

### MCP as the universal semantic-layer exit door
**First logged:** 2026-09-08 · **Last updated:** 2026-09-08 · **Status:** active — standards/consolidation

[[MCP]] isn't just a connectivity protocol anymore — it's becoming the default way vendors expose (and govern) their semantic/context layer to any agent. Microsoft's Fabric IQ Ontology got an MCP server (Preview, Aug 29), explicitly following "the same pattern already seen from Databricks and Snowflake" per the market-landscape log itself — Databricks' Genie One MCP server, Snowflake's Cortex Agents/MCP Native Apps, and (new this window) [[Market Landscape/Strategy|Strategy]] Mosaic's own MCP server all do the same thing. On the Databricks side, Unity Gateway's unified trace table (Beta, Sep 1) went a step further and turned every MCP tool call itself into a governed, queryable artifact — Databricks used it internally to catch $499K/year in wasted agent spend. Worth watching whether this tips into an actual cross-vendor MCP interop spec for semantic layers, not just parallel implementations.

**Built on:**
- Fabric IQ Ontology MCP reaches Preview (Aug 29) — [Source](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-fabric-iq-ontology)
- Unity Gateway unified trace table reaches Beta (Sep 1) — [Source](https://www.databricks.com/blog/how-we-eliminated-1-million-year-wasted-ai-agent-spend-one-hour)
- Strategy Mosaic's own MCP server (existing vault coverage, backfilled Aug 30) — [Source](https://software.strategy.com/strategyai/agents)

**Update log:**
- 2026-09-08: initial observation.

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
**First logged:** 2026-09-08 · **Last updated:** 2026-09-09 · **Status:** active — converging moves, now confirmed

Three independent vendors have now shipped near-identical persistent-memory UX within about eight weeks of each other: [[Genie One]] Memory (Beta, shipped Jul 16), Strategy AI Agents' Long-Term Memory (shipped Aug 14), and — the confirming signal this observation flagged on Sep 8 as worth watching for — ThoughtSpot's Spotter Memory reaching **GA, on by default** (Sep 9). All three land on the same design: user-reviewable, correctable, cited when used. ThoughtSpot went further than a same-shape catch-up: Spotter Memory can now be generated directly from Liveboards (not just conversation turns), and a new "Remember this" button shows a preview of the exact definition being stored before the user commits — arguably a cleaner trust/consent pattern than either Genie One's or Strategy's current implementation. With three unrelated vendors converging on the same feature within two months, this has moved past "signal to watch" — persistent memory is now a baseline expectation for any serious NL-BI agent, not a differentiator. Sigma and Fabric IQ are the two notable vendors in this vault's coverage with no shipped memory feature yet — worth checking whether they follow, and whether being last matters competitively once a capability is this normalized.

**Built on:**
- Genie One Memory, Beta, shipped Jul 16 (backfilled Sep 2) — [Source](https://docs.databricks.com/aws/en/genie-one/chat#add-to-genie-ones-memory)
- Strategy AI Agents Long-Term Memory, Aug 14 release — [Source](https://software.strategy.com/blog/august-2026-agents-that-remember-mosaic-schema-in-studio-and-personalized-bi)
- ThoughtSpot Spotter Memory reaches GA, on by default (Sep 9) — [Source](https://docs.thoughtspot.com/cloud/26.9.0.cl/notes.html)

**Update log:**
- 2026-09-08: initial observation (two vendors, flagged as pattern to watch).
- 2026-09-09: reworked — ThoughtSpot Spotter Memory GA is the third independent vendor, confirming the pattern as settled table stakes rather than an emerging trend; take changed from "watch for a confirming signal" to "confirmed, Sigma/Fabric IQ now the outliers."

---

## Retired / Superseded Observations

_None yet._

---

## Quiet Days

_Dated log-only line for each run where no new pattern, and no update to an existing observation, was found — so the record shows the day was checked rather than skipped. No entries yet; this doc's first run (2026-09-08) had four active observations._
