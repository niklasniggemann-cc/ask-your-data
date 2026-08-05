# Ask Your Data

A knowledge vault on building trustworthy natural-language data interfaces — covering Databricks Genie Agents, the infrastructure beneath them, and the engineering practices required to keep GenAI systems reliable in production.

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

These notes capture *how things work and why they're designed that way* — not step-by-step tutorials or official documentation.

## Structure

Notes are written in the [Zettelkasten](https://zettelkasten.de/) style: one concept per note, linked to related concepts. The site is built with [Quartz](https://quartz.jzhao.xyz/) from an Obsidian vault. The vault itself lives entirely under `content/` — topic folders (`Databricks/`, `Genie/`, `Semantic/`, `Frameworks/`, `AI Quality/`) plus `index.md` as the home page. Everything else in the repo (`quartz/`, config, `package.json`, etc.) is site-building code.

## How This Vault Stays Updated

This isn't a static wiki — the Databricks GenAI section keeps itself current through a scheduled agent pipeline. That automation is an integral part of this project, not a bolt-on script, so here's how it actually works.

**The general idea:** once a day, a scheduled task fires in Claude (Cowork), runs a research skill that hunts for genuinely new Databricks "Ask Your Data" / GenAI developments, and writes anything confirmed and new straight into this vault — then commits and pushes the change so the live site rebuilds. No one has to remember to check for updates or manually edit notes; the agent does the research, the deduplication, and the vault hygiene in one pass.

### 1. The research skill — `databricks-genai-daily-update`

A reusable skill definition (not specific to this vault — it could run in any chat) that encodes the actual research methodology:

- **Scope** — Genie/AI-BI, Mosaic AI, Model Serving, Vector Search, Unity Catalog AI functions, LakeFlow, MLflow GenAI tooling, DBRX, and notable third-party/open-source projects built on top of these.
- **Dedup first** — before searching anything, it establishes a baseline of what's already been reported (recent chats in the project, plus the vault's own changelog) so it never repeats old news.
- **Search broadly** — official Databricks blog/docs/release notes first, then the wider web (Reddit, Hacker News, GitHub, X) for signal official channels miss.
- **Filter hard** — only confirmed, genuinely new findings make the cut. Rumors, unverified leaks, and anything already covered (unless there's a real delta, like preview → GA) get dropped.
- **Write it down** — findings get presented as a chat briefing *and* written into the vault, following the vault's existing conventions rather than bolting on a new format.

### 2. The scheduled task

A Cowork scheduled task runs this skill automatically (currently daily). It runs non-interactively — nobody is present to answer clarifying questions — so the task carries its own operating instructions on top of the skill:

- Verify the vault is actually reachable before doing anything (read `content/index.md`; if that fails, still produce the chat briefing but skip vault writes).
- Use `content/Databricks/Updates.md` as the **authoritative dedup source**, since `recent_chats`/`conversation_search` aren't available in a scheduled (non-interactive) run.
- **Auto-create new concept notes.** The base skill's default behavior is to just *flag* a genuinely new concept in chat and let a human decide whether it deserves its own note. This vault overrides that: the scheduled task is authorized to create the note itself, following existing frontmatter/structure conventions and adding reciprocal `[[wikilinks]]` from related notes — see e.g. `content/Semantic/OntoBricks.md`.
- **Commit and push.** If anything under `content/` changed, stage only that directory (`git add content/` — never the Quartz site code), commit with a one-line summary, and push to the `v5` branch. A failed push is reported plainly rather than retried silently, so it can be fixed by hand.

### 3. What gets written to the vault

Two things get updated per finding that clears the skill's filters:

1. **The changelog** — a new dated entry gets appended (newest first) to `content/Databricks/Updates.md`. This file is append-only; past entries are never rewritten. It doubles as the dedup baseline for future runs.
2. **The relevant concept note** — if a finding updates something the vault already documents (e.g. a feature going from Preview to GA), a `## Recent Developments` entry gets added to that note directly, so the note itself stays current rather than requiring someone to cross-reference the changelog.

### 4. Publishing

A push to `v5` triggers the site's normal build/deploy (GitHub Pages via the repo's CI), so the live site picks up new entries and notes automatically, with no manual deploy step.

### Running it manually

Outside the scheduled run, the skill can be invoked in any chat with `/databricks-update` or by just asking something like "anything new on Databricks GenAI?" — it behaves the same way, except it also has access to real chat history for dedup, which the scheduled/non-interactive run doesn't.

### Why it's built this way

- **Dedup correctness matters more than speed.** Missing something because it was wrongly assumed to be a repeat is worse than a slightly slower search — the vault changelog exists specifically to make that call reliable even when chat history isn't available.
- **The vault should look hand-maintained, not bolted-on.** New notes match existing frontmatter and section conventions exactly; edits to existing notes are surgical, not restructuring.
- **Confirmed only.** The skill has no "rumors" section — if something can't be verified against a primary source, it's dropped rather than flagged as speculative.

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
