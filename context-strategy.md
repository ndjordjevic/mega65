# Strategy: Making the AI Agent MEGA65-Aware

How to give Claude Code persistent knowledge of all MEGA65 resources (websites, PDFs, GitHub repos, YouTube, Discord) without re-running web searches every session.

**TL;DR recommendation: Use your own `pin-llm-wiki` skill to build a local MEGA65 wiki in this repo, add a local PDF/LaTeX book library for the official docs, and wire it all together with a `CLAUDE.md`. Skip RAG entirely.**

---

## 1. The three options, compared

### Option A — Links only (resources.md as-is)
- **How it works:** Agent sees URLs, fetches them on demand with WebFetch/WebSearch.
- **Verdict: not enough.** Every new session pays full fetch cost again; WebFetch is lossy (small model summarizes the page); YouTube transcripts and PDF books aren't fetchable this way at all. This is exactly the token burn you want to avoid.
- Keep `resources.md` anyway — it's the human-readable catalog and the ingestion source list.

### Option B — RAG (vector database + embeddings)
- **How it works:** Chunk all sources, embed, store in a vector DB, retrieve by semantic similarity.
- **Verdict: overkill, and the wrong fit.** Reasons:
  - **Corpus size.** The MEGA65 corpus is a few dozen sources. [Below ~100k tokens of summarized notes, an agent can hold an index in context and navigate directly — no embeddings needed](https://towardsdatascience.com/how-to-build-a-claude-code-powered-knowledge-base/).
  - **Agentic search beats vector search for this workload.** By 2026, [top coding-agent systems don't rely on vector retrieval](https://buzzgrewal.medium.com/ai-agents-dont-need-vector-search-anymore-inside-the-agentic-search-stack-replacing-rag-in-2026-58efcabe4f6f); Claude Code's native loop (read index → grep → read file → retry) is [a control loop, not a one-shot pipeline](https://towardsdatascience.com/agentic-rag-vs-classic-rag-from-a-pipeline-to-a-control-loop/), and it self-corrects when the first retrieval misses.
  - **Infrastructure cost.** A vector DB is one more thing to host, re-index, and keep in sync. Markdown in git is reviewable, diffable, and free.
  - RAG starts paying off at hundreds of thousands of chunks or sub-second latency requirements — neither applies here.

### Option C — LLM wiki (Karpathy pattern via your pin-llm-wiki) ✅ **Recommended**
- **How it works:** `/pin-llm-wiki init` + `ingest` turns each URL into an immutable raw capture (`raw/`) plus a summarized, cross-linked, cited wiki page (`wiki/sources/`). `AGENTS.md` instructs every agent to consult `wiki/index.md` before answering domain questions.
- **Why it wins here:**
  - You already built and maintain the tooling (`~/LLMProjects/pin-llm-wiki`), and `agentic-ai-wiki` proves the workflow.
  - It natively handles **3 of your 5 source types**: web pages (with docs crawling + companion-repo discovery), GitHub repos, and YouTube videos (yt-dlp transcripts).
  - One-time ingestion cost, then every future session reads local markdown — near-zero marginal tokens.
  - Greppable, git-versioned, Obsidian-browsable, citable back to raw captures.

---

## 2. Where to put the wiki

**Recommendation: in this repo** (`~/retro-computers/mega65/`), not a separate repo.

- This repo *is* the MEGA65 learning project; wiki, books, notes, and future code all live together, and any session opened here is automatically wiki-aware via `AGENTS.md`/`CLAUDE.md`.
- A separate `mega65-wiki` repo (like `agentic-ai-wiki`) only makes sense if you want to publish it standalone on GitHub. If you go that route, add a pointer in this repo's `CLAUDE.md` ("consult `../mega65-wiki/wiki/index.md` for MEGA65 questions") — the same pattern `agentic-ai-wiki`'s README describes for cross-repo use.

---

## 3. Per-source-type plan

### 🌐 Websites → pin-llm-wiki `ingest` (native support)
Queue these in `inbox.md`:

```
https://mega65.org/                                  <!-- detail:deep -->
https://dansanderson.com/mega65/                     <!-- detail:deep -->
https://dansanderson.com/mega65/welcome/             <!-- the Welcome Guide, HTML version -->
https://retrocombs.com/mega65
https://retrocogs.mega65.com/
https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/
https://files.mega65.org/html/main.php               <!-- detail:brief --> <!-- catalog only -->
https://mega65.atlassian.net/wiki/spaces/MEGA65/overview  <!-- Confluence; check fetchability -->
https://www.c64-wiki.com/wiki/mega65                 <!-- detail:brief -->
```

Notes:
- `mega65.org` at deep detail may trigger companion-repo discovery (mega65-core) — that's desirable.
- The Confluence wiki may render poorly via plain fetch; if the capture is thin, rely on the official PDFs instead (they cover the same ground more authoritatively).
- The Trenz shop page is just a product listing — `detail:brief` or skip; `resources.md` already links it.

### 📦 GitHub repos → pin-llm-wiki `ingest` (native support)
```
https://github.com/MEGA65/mega65-user-guide          <!-- clone --> <!-- detail:deep -->
https://github.com/MEGA65/mega65-tools
https://github.com/MEGA65/mega65-code-snippets
https://github.com/RetroCogs/Mega65Tutorials         <!-- detail:deep -->
https://github.com/dansanderson/easyasm65
https://github.com/lgblgblgb/xemu                    <!-- detail:brief --> <!-- emulator; usage docs only -->
https://github.com/MEGA65/mega65-core                <!-- detail:brief --> <!-- FPGA internals; brief until needed -->
```

**The `mega65-user-guide` repo is the killer move for the PDF problem** — see next section.

### 📕 PDFs (the 5 official books) → local library + LaTeX source (the gap pin-llm-wiki doesn't cover)

pin-llm-wiki has no PDF ingestion. Two complementary tactics:

**Tactic 1 — greppable LaTeX source (best).** All five books are built from LaTeX in `MEGA65/mega65-user-guide`. Ingest that repo with `<!-- clone -->` (deep): the full `.tex` source lands in `raw/github/MEGA65-mega65-user-guide/`. LaTeX is plain text — the agent can `grep` for any BASIC keyword, register, or opcode and read the authoritative passage directly. This converts ~1,500 pages of PDF into searchable text for free.

**Tactic 2 — local PDF shelf for page-accurate reading.** Download the built PDFs once into `books/`:

```
books/
  mega65-user-guide.pdf        # https://mega65.org/user-guide
  mega65-developer-guide.pdf   # https://mega65.org/developer-guide
  mega65-basic65-reference.pdf # https://mega65.org/basic65-ref
  mega65-chipset-reference.pdf # https://mega65.org/chipset-ref
  mega65-book.pdf              # https://mega65.org/mega65-book (compendium; optional, it's the other 4 combined)
  INDEX.md                     # topic → book → chapter/page-range map
```

Claude Code's Read tool reads PDFs by page range (≤20 pages per request), so a small hand-made `INDEX.md` ("sprites → Chipset Ref ch. 3, pp. 45–60") makes targeted lookups cheap. Refresh the PDFs occasionally — they're rebuilt by Jenkins from latest source.

### 🎬 YouTube → expand playlists, ingest key videos individually

pin-llm-wiki ingests single videos (yt-dlp transcript + metadata) but **not playlists or channels**. Workflow:

1. Expand a playlist to video URLs once:
   ```bash
   yt-dlp --flat-playlist --print "https://www.youtube.com/watch?v=%(id)s  # %(title)s" \
     "https://www.youtube.com/playlist?list=PLPehmjqZolWArdt53pl1QyJurZDu3oJKy"
   ```
2. Cherry-pick the tutorial-dense videos (skip unboxings/news) and queue them in `inbox.md`.
3. Same for the retroCombs User's Guide series (`PLRVBh2hjFTomDGwIT7uPMJv4zH9JAUSVG`) — though their companion blog posts at retrocombs.com cover the same content as ingestable web pages, which is often the better capture.

Channels (@MEGA65retro) stay as live links in `resources.md` — ingest new videos selectively as they appear.

**Possible future enhancement to pin-llm-wiki:** a playlist handler that auto-expands via `--flat-playlist` and queues each video. Worth adding to the skill if you do this often.

### 💬 Discord → live resource, not ingestible (by design)
- Auth-walled, real-time, conversational — there is no meaningful "capture" of a Discord server, and scraping it would violate ToS.
- Treat it as the **escalation path**: the agent answers from the wiki; when the wiki doesn't know, the human asks on Discord (`#mega65`, 2000+ members).
- When a Discord thread yields a golden answer, paste it into a `wiki/sources/discord-notes.md` page (or a `notes/` file) manually — curate, don't scrape.

---

## 4. Wiring it together: CLAUDE.md

After `init`, pin-llm-wiki generates `AGENTS.md`. Add a thin `CLAUDE.md` in this repo so Claude Code sessions get the protocol automatically:

```markdown
# MEGA65 Learning Project

Before answering any MEGA65 question:
1. Read `wiki/index.md` and follow [[wikilinks]] to relevant source pages.
2. For official-spec questions (BASIC 65, VIC-IV, 45GS02 registers), grep the
   LaTeX source in `raw/github/MEGA65-mega65-user-guide/` or read the matching
   PDF pages via `books/INDEX.md`.
3. Only web-search if the wiki and books don't contain the answer; when that
   happens, queue the new source: `/pin-llm-wiki queue <url>`.
4. `resources.md` is the human-readable catalog of all known resources.
Unknowns → suggest asking on the MEGA65 Discord (link in resources.md).
```

That feedback loop in step 3 is what keeps the wiki growing instead of decaying: every cache miss becomes a future cache hit.

---

## 5. Token economics (why this beats re-searching)

| Approach | First session | Every later session |
|---|---|---|
| Links + web search | ~30–60k tokens of searches/fetches | same, every time |
| RAG | ingestion + infra setup | cheap queries, but infra upkeep + lossy chunk retrieval |
| **pin-llm-wiki** | one-time ingest cost (spread over a few `/pin-llm-wiki ingest` runs) | read `index.md` (~2–5k) + 1–2 source pages on demand |

The wiki also *improves* answer quality, not just cost: transcripts and full-page captures beat WebFetch's summarized fetches, and citations back to `raw/` make answers verifiable.

---

## 6. Setup checklist

```bash
# 1. In ~/retro-computers/mega65/
/pin-llm-wiki init                      # scaffold wiki/, raw/, inbox.md, AGENTS.md

# 2. Queue sources (paste the lists from §3 into inbox.md, or):
/pin-llm-wiki queue https://mega65.org/ https://dansanderson.com/mega65/ ...

# 3. Ingest in batches (review git diff between runs)
/pin-llm-wiki ingest

# 4. Download the PDF books into books/ and write books/INDEX.md

# 5. Expand YouTube playlists with yt-dlp, queue the keepers, ingest

# 6. Write CLAUDE.md (template in §4)

# 7. Periodically: /pin-llm-wiki lint, and <!-- refresh --> stale sources
```

---

## Sources consulted

- [How to Build a Claude Code-Powered Knowledge Base (Towards Data Science)](https://towardsdatascience.com/how-to-build-a-claude-code-powered-knowledge-base/) — the <100k-token "no RAG needed" threshold
- [Inside the Agentic Search Stack Replacing RAG in 2026 (Medium)](https://buzzgrewal.medium.com/ai-agents-dont-need-vector-search-anymore-inside-the-agentic-search-stack-replacing-rag-in-2026-58efcabe4f6f)
- [Agentic RAG vs Classic RAG: From a Pipeline to a Control Loop (Towards Data Science)](https://towardsdatascience.com/agentic-rag-vs-classic-rag-from-a-pipeline-to-a-control-loop/)
- [RAG vs. Agentic Search (Agentic Engineering Guide)](https://agents.siddhantkhare.com/06-rag-vs-agentic-search/)
- [Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) — the pattern pin-llm-wiki automates
- [Self-Maintaining Knowledge Base with Claude Code & Karpathy's LLM Wiki (HackerNoon)](https://hackernoon.com/how-i-built-a-self-maintaining-knowledge-base-for-6-projects-using-claude-code-and-karpathys-llm-wiki)
- Local: `~/LLMProjects/pin-llm-wiki/README.md` + `skills/pin-llm-wiki/` (capability check: web/GitHub/YouTube yes; PDF/playlist/Discord no), `~/LLMProjects/agentic-ai-wiki/` (reference implementation)
