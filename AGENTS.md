# MEGA65 retro computer wiki — agent instructions

> **Created:** 2026-06-10 | **Detail level:** standard (default; per-source overrides via `<!-- detail:X -->` inbox tags)

---

## For AI agents working in this repo

Answer **any question** about MEGA65 retro computer from local files first; web search is the last resort, not the first move. In order:

1. **Wiki first, then drill down on demand.** Read `wiki/index.md` to identify relevant pages, follow `[[wikilinks]]` into the relevant source pages, and cite wiki page names. A source page may be an **index of summaries** (e.g. `wiki/sources/dansanderson.com.md` lists every blog post with a one-paragraph summary and a link to its raw file). When the wiki summary answers the question, stop there. When you need more detail, follow this chain:
   **wiki page → raw page → original URL.** The raw captures under `raw/web/<site>/` are often *condensed summaries*, not verbatim copies — each begins with a `- URL:` line. If the raw summary still lacks the detail you need (exact code, full steps, a value not summarized), fetch that `- URL:` directly before falling back to a general web search.
2. **Official-spec questions** (BASIC 65 keywords, VIC-IV/45GS02/45E100 registers, memory map, DOS): grep the books' LaTeX source in `raw/github/MEGA65-mega65-user-guide/` — 87 `.tex` files, fully greppable plain text.
3. **Catalog lookups** (which tool/site/channel exists for X): `resources.md` is the human-readable catalog of all known MEGA65 resources.
4. **Only then web-search** — and say clearly that the wiki didn't cover it. When a search produces a genuinely useful new source, close the loop: `/pin-llm-wiki queue <url>` so the next session gets it for free.

This wiki is the authoritative local source for this domain. Go online for gaps or newer information rather than filling them from training data alone.

**Escalation:** if neither the wiki, the books, nor a web search settles it (e.g. hardware-revision quirks, unreleased features), suggest asking on the MEGA65 Discord (`#mega65`, link in `resources.md`) — and when the answer comes back, capture it in a wiki notes page.

> **Wiki management:** Use `/pin-llm-wiki` (`init`, `run`, `lint`, `queue`, `remove`) to ingest sources and manage this wiki. The skill runs in Claude Code, Cursor, and GitHub Copilot — full workflow instructions live in the skill files.

---

## Git — never auto-commit

**Do not** run `git commit` or `git push` after ingest, refresh, `run`, `lint`, `remove`, initial wiki scaffold, or any other file change in this repo—**unless the human explicitly asked you to commit or push in this conversation.**

When work is done, list what changed and stop; the human reviews diffs and runs `git commit` / `git push` when ready.

---

## Wiki structure

```
wiki/
  index.md          ← start here; lists every page, counts sources
  overview.md       ← rolling cross-source overview (cites [[source pages]])
  log.md            ← append-only record of every ingest/refresh
  sources/          ← one page per ingested source (<slug>.md)
  .archive/         ← soft-deleted sources (ignore unless needed)

raw/
  README.md
  github/           ← immutable GitHub repo captures
    MEGA65-mega65-user-guide/  ← full clone: greppable LaTeX source of all 5 official books
  youtube/          ← immutable YouTube video captures (transcript + metadata)
  web/              ← immutable web page/site captures

inbox.md            ← agents may add to ## Pending via `queue`; all other edits are human-driven
.pin-llm-wiki.yml   ← config (detail level, source types, lint cadence, etc.)
resources.md        ← human-readable catalog of all known MEGA65 resources
context-strategy.md ← why this knowledge layer exists and how it is designed
CLAUDE.md           ← Claude Code adapter (imports this file via @AGENTS.md)
```

**Load order for any question:** `wiki/index.md` → relevant source page(s) → raw page (summary or capture; carries a `- URL:`) → original URL if the raw still lacks the needed detail.

> **Raw is not always verbatim.** Most `raw/` files are near-verbatim captures, but some web sources (notably the dansanderson.com Digest articles) are stored as condensed summaries to save space. Treat the `- URL:` at the top of each raw page as the authoritative full text and fetch it when a summary is insufficient. Never edit `raw/` — it is immutable.

## Housekeeping

- Never edit anything under `raw/` — immutable captures.
- `inbox.md` `## Pending` is the source queue; ingest with `/pin-llm-wiki run`.
- YouTube playlists can't be ingested directly: expand with
  `yt-dlp --flat-playlist --print "https://www.youtube.com/watch?v=%(id)s  # %(title)s" <playlist-url>`
  and queue the tutorial-dense videos individually.
