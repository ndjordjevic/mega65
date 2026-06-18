# MEGA65 learning project — Claude Code adapter

@AGENTS.md

**All canonical instructions live in `AGENTS.md`** (shared with Cursor/Copilot): the answer protocol (wiki → official-spec grep → `resources.md` → web), the wiki→raw→original-URL drill-down chain, Discord escalation, the **accuracy discipline** (cite load-bearing claims; prefer User's-Guide greps over web; qualify anything that varies by board revision R1–R6 / model / core version — the "three FPGAs vs two" slip), housekeeping, and the never-auto-commit git policy. Follow them exactly. Design rationale: `context-strategy.md`.

This file holds **only the Claude-Code-specific tool mechanics** that must not leak into the shared `AGENTS.md` (where Claude-only tool names would confuse Cursor/Copilot):

- **WebFetch for drill-down** — a raw page under `raw/web/` may be a condensed summary; when it lacks a needed detail, use **WebFetch** on its `- URL:` line before a general web search (the wiki→raw→original chain in `AGENTS.md`).
- **Skills** — when the user types `/pin-llm-wiki ...` (or any skill), invoke it via the **Skill** tool.
- **Live Discord search** (see "Searching the MEGA65 Discord" in `AGENTS.md`): the `mcp__playwright__browser_*` tools from the project-local `playwright` MCP are **deferred** — fetch their schemas with `ToolSearch` (e.g. `select:mcp__playwright__browser_navigate,mcp__playwright__browser_click,mcp__playwright__browser_type,mcp__playwright__browser_snapshot,mcp__playwright__browser_wait_for`) before calling them. The search-result snapshot is large — persist it and `grep` the `region "Search Results"` block rather than reading the whole thing (or take a screenshot, which reads more reliably than parsing the snapshot YAML). Follow the reformulate-and-retry loop and the low-signal/no-bulk-scrape rules in `AGENTS.md`.
