# Ask Your Data

A knowledge vault on building trustworthy natural-language data interfaces — covering Databricks Genie Agents, the infrastructure beneath them, the engineering practices required to keep GenAI systems reliable in production, and the broader "ask your data" market landscape across every other vendor in the space.

**Live site: https://niklasniggemann-cc.github.io/ask-your-data/**

---

## What's Inside

| Area | Topics |
|------|--------|
| **Genie** | Genie Agents, Genie One, Genie Code, Knowledge Store |
| **Databricks** | Unity Catalog, Agent Metadata, Medallion Architecture, Data Quality, Delta Lake |
| **Semantic** | Semantic Layer, NL-to-SQL, Disambiguation, Data Governance, Data Lineage |
| **AI Quality** | Data Flywheel, Evaluation, LLM-as-a-Judge, GenAI Technical Debt, Observability |
| **Frameworks** | MLflow, LangGraph, DSPy, MCP |
| **Market Landscape** | Snowflake CoWork/Cortex, ThoughtSpot Spotter, Looker/BigQuery Conversational Analytics, Amazon Quick Suite, Fabric IQ/Copilot for Power BI, Tableau Next, Sigma, TextQL, dbt Semantic Layer, Open Semantic Interchange, text-to-SQL open source |

These notes capture *how things work and why they're designed that way* — not step-by-step tutorials or official documentation.

## Structure

Notes are written in the [Zettelkasten](https://zettelkasten.de/) style: one concept per note, linked to related concepts. The site is built with [Quartz](https://quartz.jzhao.xyz/) from an Obsidian vault. The vault itself lives entirely under `content/` — topic folders (`Databricks/`, `Genie/`, `Semantic/`, `Frameworks/`, `AI Quality/`, `Market Landscape/`) plus `index.md` as the home page. Everything else in the repo (`quartz/`, config, `package.json`, etc.) is site-building code.

## How This Vault Stays Updated

This isn't a static wiki — it keeps itself current through one scheduled agent run per day. That automation is an integral part of this project, not a bolt-on script, so here's how it actually works.

**The general idea:** once a day, a single scheduled task fires in Claude (Cowork) — "Data Landscape Daily Digest." It covers two disjoint corners of the "ask your data" world back-to-back (Databricks GenAI, then the rest of the market), each with its own scope and dedup logic, then wraps up with one combined chat briefing and **one** git commit/push for whatever changed under `content/`. No one has to remember to check for updates or manually edit notes; the agent does the research, the deduplication, the verification, and the vault hygiene in a single pass.

This task is a merge of two formerly-separate scheduled tasks (`databricks-daily` and `ask-your-data-landscape-daily`). They're kept internally distinct — different scope, different dedup baseline, different vault files — specifically so their coverage never blends together, but the wrapper task treats them as sections of one run rather than two independent jobs.

### 0. Before anything else: confirm the vault is reachable

Because the run is unattended, it can't call an interactive folder-access prompt — nobody's there to click "approve." So the first thing the task does is try to `Read` `content/index.md` directly. If that succeeds, the vault is reachable and both sections proceed as normal, writing to the vault as described below. If it fails, the task still produces both research briefings from web search alone, states plainly in the chat summary what it tried and why the vault was unreachable, and skips every vault-write and git step for that run.

### 1. Section A — Databricks GenAI, via the `databricks-genai-daily-update` skill

A reusable skill definition (not specific to this vault — it could run in any chat) that encodes the actual research methodology:

- **Scope** — Genie/AI-BI, Mosaic AI, Model Serving, Vector Search, Unity Catalog AI functions, LakeFlow, MLflow GenAI tooling, DBRX, and notable third-party/open-source projects built on top of these.
- **Dedup first** — before searching anything, it reads `content/Databricks/Updates.md` **in full** (not just the latest entry) as the dedup baseline. `recent_chats`/`conversation_search` aren't available in a scheduled run, so the vault's own changelog is treated as authoritative rather than a supplement to chat history.
- **Search broadly** — official Databricks blog/docs/release notes first (fetched directly rather than trusted from search snippets, which have repeatedly proven stale or wrong), then the wider web (Reddit, Hacker News, GitHub, X) for signal official channels miss.
- **Filter hard** — only confirmed, genuinely new findings make the cut. Rumors, unverified leaks, and anything already covered (unless there's a real delta, like preview → GA) get dropped.
- **Verify before writing** (the skill's own Step 5) — every finding that survives the filter gets a second, independent confirming pass — re-fetching the primary source directly, not re-reading the first search snippet — before it's written anywhere. Vault entries are never deleted once written, so this cost is treated as worth paying every run rather than skipped to save time.
- **Auto-create new concept notes.** When a finding introduces a genuinely new concept with no existing note anywhere in the vault, the task creates the note itself rather than just flagging it in chat — following existing frontmatter/structure conventions exactly and adding reciprocal `[[wikilinks]]` from related notes (see e.g. `content/Semantic/OntoBricks.md`). Because "create a note" is a higher-stakes, harder-to-undo call than a log line, it gets the harder version of the verification pass: a second independent source where practical, plus an actual vault search for the concept's name and variants — not just a skim of the likely folder.

### 2. Section B — Market Landscape (everything but Databricks)

Same shape, different scope: Snowflake Cortex Analyst/Intelligence/CoWork, ThoughtSpot (Spotter), Looker/BigQuery Conversational Analytics, Amazon Quick Suite, Microsoft Copilot for Power BI/Fabric IQ, Tableau Next/Pulse, Sigma, Omni, Hex, Metabase, dbt Semantic Layer and other semantic-layer players (Cube, AtScale), text-to-SQL startups/OSS (Seek AI, DataChat, Vanna AI, WrenAI, TextQL, etc.), and cross-vendor industry trends (Gartner adoption stats, standards like Open Semantic Interchange). Explicitly scoped to **exclude** Databricks — a story that's fundamentally a Databricks story gets skipped here even if it's tempting to include, since Section A already owns that ground.

- **Dedup baseline:** `content/Market Landscape/Updates.md`, read in full first — same "vault changelog as source of truth" logic as Section A.
- **Same filters, plus one more:** confirmed-only and genuinely-new-only, and — specific to this section — funding rounds, valuations, and market-size dollar figures are explicitly out of scope even when they're the vehicle for a real product update; only the product substance gets kept.
- **Same verification pass**, run inline rather than as a separate skill step: confirm the date and status (Beta/Preview/GA) against the primary source itself, re-read the source to confirm it actually supports the summary, and run one more targeted dedup check against the changelog for that specific finding's keywords, since near-duplicates can hide under different phrasing.
- **New-concept notes, but with judgment rather than a hard rule.** This section covers far more vendors than Section A, so most incremental features stay log-only. A note only gets created for a genuinely significant new product, platform, or standalone concept likely to accumulate further coverage — e.g. `content/Market Landscape/TextQL.md`, created after confirming TextQL was a real, explicitly-in-scope gap (never researched despite being named in the skill's own scope list) via a second independent source (Gartner Peer Insights) and an actual vault search for the name. A vendor that's notable but not clearly note-worthy yet gets flagged in chat instead.
- **Periodic backfill check.** Beyond same-day news, the task occasionally checks whether an in-scope vendor has simply never been researched — a missing baseline entry isn't the same as "nothing new." This is how Amazon Quick Suite, Fabric IQ, Looker Conversational Analytics, and TextQL all ended up backfilled well after they'd actually shipped.

### 3. What gets written to the vault

Per finding that clears a section's filters:

1. **The changelog** — a new dated entry gets appended (newest first) to that section's `Updates.md` (`content/Databricks/Updates.md` or `content/Market Landscape/Updates.md`). Both files are append-only; past entries are never rewritten or deleted, which is also why the verification pass above exists — a wrong entry is effectively permanent.
2. **The relevant concept note** — if a finding updates something the vault already documents (e.g. a feature going from Preview to GA), a `## Recent Developments` entry gets added to that note directly, regardless of which section surfaced it — the vault doesn't care which half of the run wrote a given line, only that cross-links stay reciprocal.

### 4. One combined summary, one commit, one push

The two sections stay firmly separate internally (scope, dedup, vault files), but the run ends as a single unit:

- **Chat summary** — two clearly labeled parts (Databricks, then Market Landscape), each skimmable prose with light bullets, explicit deltas flagged, "nothing new" stated plainly when true, and any corrections the verification pass made called out so that step's value is visible rather than invisible.
- **Git commit/push** — only if either section actually wrote something. `git add content/` only (never the Quartz site code), one commit covering both sections' changes with a one-line summary, `git pull --rebase origin v5`, then `git push origin v5`. A failed push is reported plainly rather than retried or discarded silently.
- **A known FUSE-mount quirk.** The vault's mount supports `rename()` but not `unlink()`, which breaks git's normal lock-file protocol (create-then-delete) and leaves stale `.git/index.lock`-style files that block every later git call. The task works around this every run: rename (never delete) any stale lock files first, then point `GIT_INDEX_FILE` at a normal-filesystem path (`/tmp/aud-index`, seeded from `HEAD`) for the rest of the git commands, which sidesteps the broken index-lock path entirely. Harmless `warning: unable to unlink ...` lines on object tmp-files and lock files are expected noise as long as the commit itself reports success.

A push to `v5` then triggers the site's normal build/deploy (GitHub Pages via the repo's CI), so the live site picks up new entries and notes automatically, with no manual deploy step.

### Running it manually

Outside the scheduled run, either section's research can be invoked ad hoc in any chat: `/databricks-genai-daily-update` (or "anything new on Databricks GenAI?") for Section A, or by asking about conversational BI / natural-language analytics vendors for Section B. Run manually, they behave the same way except they also have access to real chat history for dedup, and can ask clarifying questions — neither is available to the unattended scheduled run.

### Why it's built this way

- **Dedup correctness matters more than speed.** Missing something because it was wrongly assumed to be a repeat is worse than a slightly slower search — the vault changelog exists specifically to make that call reliable even when chat history isn't available.
- **Verification is a permanent-writes tax, and worth paying.** Nothing in the changelogs ever gets deleted, so a second confirming pass before every write — not just a first-pass search snippet — is treated as mandatory, not optional polish.
- **The vault should look hand-maintained, not bolted-on.** New notes match existing frontmatter and section conventions exactly; edits to existing notes are surgical, not restructuring.
- **Confirmed only.** Neither section has a "rumors" section — if something can't be verified against a primary source, it's dropped rather than flagged as speculative.

## Local Development

```bash
npm install
npx quartz build --serve
# → http://localhost:8080
```

## Sponsors

<p align="center">
  <a href="https://github.com/sponsors/jackyzha0">
    <img src="https://cdn.jsdelivr.net/gh/jackyzha0/jackyzha0/sponsorkit/sponsors.svg" />
  </a>
</p>
