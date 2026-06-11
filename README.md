# MEGA65 retro computer wiki

A personal knowledge base for **MEGA65 retro computer**, maintained with [pin-llm-wiki](https://github.com/ndjordjevic/pin-llm-wiki).

## What's in here

Every source is fetched, summarized, and cross-referenced so you and any AI agent can query it without re-reading the originals.

```
wiki/index.md       ← start here; full source list
wiki/overview.md    ← rolling cross-source overview
wiki/sources/       ← one page per ingested source
raw/                ← immutable source captures; do not edit
raw/github/MEGA65-mega65-user-guide/
                    ← full clone: greppable LaTeX source of all 5 official books
raw/assets/         ← official PDF books (User's Guide, BASIC 65 Ref, Dev Guide,
                       Chipset Ref, Compendium); index in raw/assets/README.md
inbox.md            ← drop new URLs under ## Pending
AGENTS.md           ← canonical instructions for agents (answer protocol lives here)
CLAUDE.md           ← Claude Code adapter; imports AGENTS.md via @AGENTS.md
.pin-llm-wiki.yml   ← config: domain, detail level, source types, lint cadence
resources.md        ← human-readable catalog of all known MEGA65 resources
context-strategy.md ← why this wiki exists and how the knowledge layer is designed
```

## Other repos

If you ask questions from **another repo** but want agents to use this wiki, add that instruction there—in `CLAUDE.md` or `AGENTS.md`—to consult this wiki's `wiki/index.md` (and follow `[[wikilinks]]`) for **MEGA65 retro computer**.

## Adding sources

**Ingest immediately** (auto-queues if missing, then fetches + writes the wiki page):
```
/pin-llm-wiki run https://github.com/org/repo
```

**Queue for later** (adds to inbox, no fetch — good for mid-task suggestions):
```
/pin-llm-wiki queue https://example.com
```

**Batch-process everything pending** in `inbox.md`:
```
/pin-llm-wiki run              # process all pending items
/pin-llm-wiki run <url>        # process only this one URL from Pending
```

**GitHub non-root pages are treated as single-page web sources.** A URL like `https://github.com/org/repo/tree/main/path` is ingested as the exact page only, with no docs discovery and no companion-repo discovery.

**Deep multi-product mode.** A web source ingested at `<!-- detail:deep -->` whose docs/site advertise ≥2 distinct products (each with its own docs subsection or distinct GitHub repo) writes one umbrella page plus one sub-page per product, all citing the same raw file.

## Inline inbox tags

Append these HTML comments to any URL line in `inbox.md`:

| Tag | Effect |
|---|---|
| `<!-- detail:brief -->` / `<!-- detail:standard -->` / `<!-- detail:deep -->` | Override detail level for this source |
| `<!-- branch:dev -->` | GitHub: use this branch instead of the default |
| `<!-- clone -->` | GitHub deep: full `git clone` to `raw/github/<org>-<repo>/` |
| `<!-- skip -->` | Skip this URL on the next `run` |
| `<!-- companion:github.com/<org>/<repo> -->` | Web: skip GitHub discovery, use this repo as the companion |
| `<!-- no-companion -->` | Web: suppress companion GitHub fetch even if a repo is found |
| `<!-- note: text -->` | Freeform note for human review (queue only; ignored by ingest) |

## Querying the wiki

Open `wiki/index.md` for the full source table, then follow `[[wikilinks]]` into source pages. Use `wiki/overview.md` for a cross-source synthesis.

AI agents in this repo follow the answer protocol in `AGENTS.md`: wiki first, then the official spec (LaTeX grep in `raw/github/MEGA65-mega65-user-guide/` or PDF pages in `raw/assets/`), then `resources.md`, and only then the web.

Raw files under `raw/` are the citation backstop. Prefer the wiki pages for normal reading; use raw captures when you need to verify source text directly.

## Maintenance

```
/pin-llm-wiki lint          # health checks (citations, orphans, stale sources, ...)
/pin-llm-wiki remove <slug> # soft-delete a source to wiki/.archive/
```

To refresh a source, add `<!-- refresh -->` to its line under `## Completed` in `inbox.md`, then run:

```
/pin-llm-wiki run
```

## Git

Agents never commit automatically. Review `git diff`, then commit when ready:
```
git add -p
git commit -m "ingest: <slug>"
```
