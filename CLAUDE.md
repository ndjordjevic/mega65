# MEGA65 learning project — Claude Code adapter

@AGENTS.md

All agent instructions live in `AGENTS.md` (canonical, shared with Cursor/Copilot): the answer protocol (wiki → official-spec grep → `resources.md` → web), the wiki→raw→original-URL drill-down chain, Discord escalation, housekeeping, and the never-auto-commit git policy. Follow them exactly. The design rationale for this knowledge layer is in `context-strategy.md`.

Claude Code specifics:

- A raw page under `raw/web/` may be a condensed summary. When it lacks a needed detail, use **WebFetch** on the `- URL:` line at the top of that raw page before doing a general web search (per the wiki→raw→original chain in `AGENTS.md`).
- When the user types `/pin-llm-wiki ...`, invoke it via the Skill tool.
- **Live Discord search** (see "Searching the MEGA65 Discord" in `AGENTS.md`): the tools are the `mcp__playwright__browser_*` set from the project-local `playwright` MCP. These are **deferred** — fetch their schemas with `ToolSearch` (e.g. `select:mcp__playwright__browser_navigate,mcp__playwright__browser_click,mcp__playwright__browser_type,mcp__playwright__browser_snapshot,mcp__playwright__browser_wait_for`) before calling them. The search-result snapshot is large; persist it and `grep` the `region "Search Results"` block rather than reading the whole thing. Follow the reformulate-and-retry loop and the low-signal/no-bulk-scrape rules in `AGENTS.md`.
- **Accuracy discipline (lessons & answers):** before stating a fact, follow "Accuracy discipline — verify before teaching" in `AGENTS.md` — cite load-bearing claims, prefer User's Guide/official-doc greps over web summaries for hardware/spec facts, and **qualify anything that varies by board revision (R1–R6) / model / core version**. The "three FPGAs vs two" slip (true for R2/R3, wrong for R6) is the canonical error to avoid; don't present pedagogical simplifications as sourced fact.
