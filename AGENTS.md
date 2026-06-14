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

**Escalation:** if neither the wiki, the books, nor a web search settles it (e.g. hardware-revision quirks, unreleased features), you can **search the MEGA65 Discord live** (see below) before suggesting the human ask there. When an answer comes back — from your search or from the human asking — capture it in a wiki notes page.

---

## Searching the MEGA65 Discord (live, via Playwright)

The agent can search the MEGA65 Discord server on demand by driving a logged-in browser — **no bot, no token, no admin rights**. This is a **read-only lookup tool**, used *after* the wiki/books/web steps above (it sits at the same stage as web search, for community knowledge that isn't written down anywhere else).

**Setup (one-time, already done):** a project-local `playwright` MCP server is registered in `~/.claude.json` for this repo. It runs its own Chromium with a **persistent profile**, so the human's Discord login survives between sessions. If the browser is **not** logged in, stop and ask the human to log in (navigate to `https://discord.com/login`, let them sign in, then continue) — never attempt to log in on their behalf.

**How to run a search:**

1. Navigate to the MEGA65 server: `https://discord.com/channels/719326990221574164` (server ID `719326990221574164`).
2. Click the search box — selector `div[role="combobox"][aria-label="Search"]` — type the query, submit with Enter.
3. Wait ~2.5s, snapshot, and read the **`region "Search Results"`** part of the snapshot (the channel message list in the background is *not* the results). The header reads `N Results` or `No Results`.
4. Report: the link/answer found, which channel + author + date it came from, and a quoted snippet.

**Reformulate-and-retry (do this automatically):** Discord search is **keyword AND-matching, not semantic** — it finds words, not intent. If a query returns `No Results` or weak hits, retry a few times, varying:
- **Fewer / core keywords** (`getting started` → `start`; multi-word phrases often match nothing).
- **Synonyms** (`beginner` → `new`, `noob`; `hardware` → `board`, `revision`, `R6`).
- **Domain terms a MEGA65 dev would actually type** (`DMA bug` → `DMAgic`; `SD card` → `SDcard`).
- **Operators** to narrow/widen: `in:#channel`, `from:user`, `has:link`.

Cap at a handful of reformulations unless the human says "keep trying." **Show the queries you tried and their hit counts**, and distinguish a *search-limitation miss* (the words aren't there) from a *real absence* — never fabricate an answer from a miss. For **intent** questions ("where do I start?") say upfront that keyword search is the wrong instrument and point to the better source (server channel structure, pinned posts, or the local wiki / User's Guide).

**Risk & scope — stay low-signal:** this works *because* it's the human's real login at human pace through the official web client. Keep it that way: a few searches per session is fine. **Do not** bulk-scrape or auto-scroll whole channels, and **do not** use user-token exporters (e.g. DiscordChatExporter) — Discord actively enforces against scripted/high-volume user-token access (account logout + ToS-abuse flags). **Do not ingest** Discord content into the wiki unless the human explicitly asks; this tool is for live lookups, not harvesting.

> **Wiki management:** Use `/pin-llm-wiki` (`init`, `run`, `lint`, `queue`, `remove`) to ingest sources and manage this wiki. The skill runs in Claude Code, Cursor, and GitHub Copilot — full workflow instructions live in the skill files.

---

## Accuracy discipline — verify before teaching (and answering)

The canonical mistake to prevent: stating a **board-revision-specific fact as universal truth** (we once wrote "the MEGA65 has three FPGAs" — true for R2/R3, but the current R6 has two; the MAX10 was removed at R4). A generic web search will not catch this — it even reported "3 FPGAs." Rules:

1. **Cite every load-bearing claim.** If a fact matters to a lesson or answer and you can't point to a source, don't assert it — drop it or mark it "unverified, to confirm." No parametric guesses dressed as fact. (The `teach` skill already requires this; follow it strictly.)
2. **Prefer the authoritative primary for the claim type.** Follow the source order above (wiki → User's Guide grep → web → live Discord). For hardware / register / memory-map / model specifics, **grep the User's Guide and official docs before trusting a web-search summary** — primaries are revision-aware; web summaries flatten that distinction.
3. **Qualify anything that varies.** Facts that depend on **board revision (R1–R6), model, core/ROM/Hypervisor version, or toolchain** must carry that qualifier — never state them as universal. If you don't know which revision/version a source describes, find out before asserting.
4. **Separate fact from framing.** Pedagogical simplifications and opinions ("only X matters") are not facts — flag them as such or omit them. Don't let an editorial shortcut read as a sourced claim.
5. **Corroborate load-bearing or shaky claims.** When a central claim rests on a single weak source, or sources disagree, confirm with a second (User's Guide / web / live Discord) before it ships. Targeted, not blanket — corroborate what's important or uncertain, not every trivially-true sentence.

When a check surfaces a genuinely new, high-quality source, queue it (`/pin-llm-wiki queue <url>`) per the standing wiki-update practice.

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
