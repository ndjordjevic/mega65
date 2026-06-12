# MEGA65 learning project — Claude Code adapter

@AGENTS.md

All agent instructions live in `AGENTS.md` (canonical, shared with Cursor/Copilot): the answer protocol (wiki → official-spec grep → `resources.md` → web), the wiki→raw→original-URL drill-down chain, Discord escalation, housekeeping, and the never-auto-commit git policy. Follow them exactly. The design rationale for this knowledge layer is in `context-strategy.md`.

Claude Code specifics:

- A raw page under `raw/web/` may be a condensed summary. When it lacks a needed detail, use **WebFetch** on the `- URL:` line at the top of that raw page before doing a general web search (per the wiki→raw→original chain in `AGENTS.md`).
- When the user types `/pin-llm-wiki ...`, invoke it via the Skill tool.
