# How This Vault Stays Updated

This vault doesn't just sit still — a scheduled agent run keeps the Databricks
GenAI section current automatically. This doc explains how that pipeline
works, for anyone (including future-me) trying to understand why entries show
up in `content/Databricks/Updates.md` without anyone manually writing them.

## The general idea

Once a day, a scheduled task fires in Claude (Cowork), runs a research skill
that hunts for genuinely new Databricks "Ask Your Data" / GenAI developments,
and writes anything confirmed and new straight into this vault — then commits
and pushes the change so the live site rebuilds. No human has to remember to
check for updates or manually edit notes; the agent does the research,
the deduplication, and the vault hygiene in one pass.

## The pieces

### 1. The skill: `databricks-genai-daily-update`

This is a reusable skill definition (not specific to this vault — it could
run in any chat) that encodes the actual research methodology:

- **Scope** — what counts as in-scope: Genie/AI-BI, Mosaic AI, Model Serving,
  Vector Search, Unity Catalog AI functions, LakeFlow, MLflow GenAI tooling,
  DBRX, and notable third-party/open-source projects built on top of these.
- **Dedup first** — before searching anything, it establishes a baseline of
  what's already been reported (recent chats in the project, plus the vault's
  own changelog) so it never repeats old news.
- **Search broadly** — official Databricks blog/docs/release notes first,
  then the wider web (Reddit, Hacker News, GitHub, X) for signal official
  channels miss.
- **Filter hard** — only confirmed, genuinely new findings make the cut.
  Rumors, unverified leaks, and anything already covered (unless there's a
  real delta, like preview → GA) get dropped.
- **Write it down** — findings get presented as a chat briefing *and* written
  into the vault (see below), following the vault's existing conventions
  rather than bolting on a new format.

### 2. The scheduled task

A Cowork scheduled task runs this skill automatically (currently daily). It
runs non-interactively — nobody is present to answer clarifying questions —
so the task carries its own operating instructions on top of the skill:

- Verify the vault is actually reachable before doing anything (read
  `content/index.md`; if that fails, still produce the chat briefing but skip
  vault writes).
- Use `content/Databricks/Updates.md` as the **authoritative dedup source**,
  since `recent_chats`/`conversation_search` aren't available in a scheduled
  (non-interactive) run.
- **Auto-create new concept notes.** The base skill's default behavior is to
  just *flag* a genuinely new concept in chat and let a human decide whether
  it deserves its own note. This vault overrides that: the scheduled task is
  authorized to create the note itself, following existing frontmatter/
  structure conventions and adding reciprocal `[[wikilinks]]` from related
  notes — see e.g. `content/Semantic/OntoBricks.md`.
- **Commit and push.** If anything under `content/` changed, stage only that
  directory (`git add content/` — never the Quartz site code), commit with a
  one-line summary, and push to the `v5` branch. A failed push is reported
  plainly rather than retried silently, so it can be fixed by hand.

### 3. The vault (`content/`)

This repo is a git-backed [Quartz](https://quartz.jzhao.xyz/) site. The
Obsidian vault itself lives entirely under `content/` — topic folders
(`Databricks/`, `Genie/`, `Semantic/`, `Frameworks/`, `AI Quality/`) plus
`index.md` as the home page. Everything else in the repo (`quartz/`, config,
`package.json`, etc.) is site-building code the daily update never touches.

Two things get updated per finding that clears the skill's filters:

1. **The changelog** — a new dated entry gets appended (newest first) to
   `content/Databricks/Updates.md`. This file is append-only; past entries
   are never rewritten. It doubles as the dedup baseline for future runs.
2. **The relevant concept note** — if a finding updates something the vault
   already documents (e.g. a feature going from Preview to GA), a
   `## Recent Developments` entry gets added to that note directly, so the
   note itself stays current rather than requiring someone to cross-reference
   the changelog.

### 4. Publishing

A push to `v5` triggers the site's normal build/deploy (GitHub Pages via the
repo's CI), so the live site at
https://niklasniggemann-cc.github.io/ask-your-data/ picks up new entries and
notes automatically, with no manual deploy step.

## Running it manually

Outside the scheduled run, the skill can be invoked in any chat with
`/databricks-update` or by just asking something like "anything new on
Databricks GenAI?" — it behaves the same way, except it also has access to
real chat history for dedup, which the scheduled/non-interactive run doesn't.

## Why it's built this way

The design leans on a few principles worth calling out explicitly:

- **Dedup correctness matters more than speed.** Missing something because it
  was wrongly assumed to be a repeat is worse than a slightly slower search —
  the vault changelog exists specifically to make that call reliable even
  when chat history isn't available.
- **The vault should look hand-maintained, not bolted-on.** New notes match
  existing frontmatter and section conventions exactly; edits to existing
  notes are surgical, not restructuring.
- **Confirmed only.** The skill has no "rumors" section — if something can't
  be verified against a primary source, it's dropped rather than flagged as
  speculative.
