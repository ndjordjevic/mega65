---
type: log
domain: "MEGA65 retro computer"
created: 2026-06-10
---

# MEGA65 retro computer wiki — log

Append-only record of all ingests, refreshes, and significant changes. Newest entries at top.

---

## 2026-06-12 | housekeeping | raw/assets/ removed — PDFs redundant with LaTeX clone

- Deleted: raw/assets/ (6 PDFs, ~161MB) — all content is in raw/github/MEGA65-mega65-user-guide/ (285 source images + 87 .tex files)
- Updated: AGENTS.md, CLAUDE.md, README.md (removed PDF references, updated spec lookup protocol)
- Updated: wiki/sources/wiebow.mega65.com.md, retrocogs.mega65.com.md, commodore-65-wikipedia.md, MEGA65-mega65-rom-public.md, dansanderson-mega65-symbols.md (raw/assets/ → [[MEGA65-mega65-user-guide]])

## 2026-06-12 | remove | c64-wiki.com | soft-deleted (redundant after commodore-65-wikipedia ingest)

- Reason: content fully covered by [[commodore-65-wikipedia]] (lineage) + [[MEGA65-mega65-user-guide]] (specs); only unique value was two benchmark figures, not worth a separate source
- Archived: wiki/sources/c64-wiki.com.md → wiki/.archive/sources/c64-wiki.com.md
- Archived: raw/web/c64-wiki.com.md → wiki/.archive/raw/web/c64-wiki.com.md
- Updated: wiki/index.md (17 sources), wiki/overview.md, wiki/log.md

## 2026-06-12 | refresh | mega65.atlassian.net | expanded from brief to full section + page index

- Previous: top-level nav only (overview page, partially blocked by Confluence JS rendering)
- Method: Confluence REST API (anonymous) — fetched child pages per section reliably where HTML rendering failed
- Created: raw/web/mega65.atlassian.net/space-structure.md (full page index: 9 sections, 66+ pages with IDs + URLs)
- Updated: wiki/sources/mega65.atlassian.net.md → complete index with per-section tables and 1–2 sentence description per page
- Updated: wiki/index.md (detail_level: brief → standard)

## 2026-06-11 | ingest | commodore-65-wikipedia | C65 prototype history + specs (background reference)

- From dansanderson.com intro-paragraph link audit; user requested ingest
- Created: raw/web/commodore-65-wikipedia.md, wiki/sources/commodore-65-wikipedia.md
- Captures the original C65 (C64DX) the MEGA65 recreates: CSG 4510 @3.54MHz, VIC-III, dual SID, BASIC 10.0; cancelled 1991; MEGA65 project from 2015
- Updated: wiki/index.md (18 sources)

## 2026-06-11 | ingest | MEGA65-mega65-rom-public | official ROM issue tracker + BASIC 65/KERNAL changelog

- From dansanderson.com intro-paragraph link audit (MEGA65 ROM link)
- Finding: repo is a *public issue tracker* for the closed-source ROM — not ROM source; value is CHANGELOG.md (authoritative BASIC 65/KERNAL version history)
- Created: raw/github/MEGA65-mega65-rom-public.md, wiki/sources/MEGA65-mega65-rom-public.md
- Other intro links already covered (mega65.org, mega65-core, Confluence docs, c64-wiki); Commodore 64 Wikipedia skipped as redundant with c64-wiki.com

## 2026-06-11 | ingest | dansanderson-mega65-symbols | I/O register symbol generator (from a dansanderson.com projects-list audit)

- Audited dansanderson.com's "other MEGA65 projects" link list against the wiki: Welcome Guide, Digest, EasyAsm, User's Guide all already covered; Mastodon bot + Zazzle merch correctly excluded (feed/commerce, in resources.md)
- Gap found + ingested: github.com/dansanderson/mega65-symbols — generates I/O register symbol files (ACME/Kick/ca65/cc65/Ophis/Rust) from iomap.txt (built from mega65-core VHDL)
- Created: raw/github/dansanderson-mega65-symbols.md, wiki/sources/dansanderson-mega65-symbols.md
- Updated: wiki/index.md (16 sources)

## 2026-06-11 | refresh | wiebow.mega65.com | restructured raw into per-post folder + captured all 3 posts (kept — concrete cross-dev pipeline)

- Reviewed for usefulness: the cross-development guide is the most copy-pasteable build pipeline in the wiki (Ethernet deploy specifics not found elsewhere). Kept.
- Discovered 2 uncaptured posts on the (now-dormant) blog; captured both
- Converted raw/web/wiebow.mega65.com.md → raw/web/wiebow.mega65.com/ folder (3 files): cross-development.md (near-verbatim, full make.sh + code), hardware-system-and-concepts.md (5-layer architecture, HYPPO, Freezer), the-mega-discovery.md (intro, no tech)
- Updated: wiki/sources/wiebow.mega65.com.md → index with a 3-post table (newest first)

## 2026-06-11 | refresh | retrocogs.mega65.com | restructured raw into per-post folder (kept — register-level VIC-IV reference)

- Reviewed for usefulness: small (5 posts) but unique register-level VIC-IV graphics tutorials; revived Aug 2025 (FCM/NCM, RRB). Kept rather than removed.
- Converted raw/web/retrocogs.mega65.com.md → raw/web/retrocogs.mega65.com/ folder (5 files), one per post
- Kept content near-verbatim (full register details + Kick Assembler code), not condensed — the author intends a living reference
- Updated: wiki/sources/retrocogs.mega65.com.md → index with a posts table (newest first); tightened the framing (it overlaps dansanderson concepts + RetroCogs-Mega65Tutorials code, unique value is the register-level prose)

## 2026-06-11 | refresh | retrocombs.com | restructured raw into per-post folder + captured all 32 blog posts

- Converted raw/web/retrocombs.com.md → raw/web/retrocombs.com/ folder (34 files)
- Site sections: resource-page.md (the link hub), users-guide-series.md (UG series index)
- Blog: all 32 retroCombs posts captured as individual summary .md files (2020-12 → 2024-08), incl. the 5-chapter User's Guide Series
- Scope decision: dansanderson pattern applied to retroCombs' *own* content only; the external link directory (Cores/Tools/Gear/etc.) is summarized in resource-page.md, not given per-link raw pages (overlaps resources.md)
- Updated: wiki/sources/retrocombs.com.md → index with one-line summary + link per post; Blog table is the complete 32 in /mega65-blog order (newest first); site sections + external directory as separate sections

## 2026-06-11 | refresh | dansanderson.com | restructured raw + captured the complete Digest

- Converted raw/web/dansanderson.com.md → raw/web/dansanderson.com/ folder (53 files)
- Site sections: hub.md, welcome-guide.md
- Digest: all 44 posts captured as individual summary .md files (no longer skipping the 11 admin/announcement posts — several carry technical nuggets: Tall Character Mode, Z-machine/Ozmoo, Pascal65, C65 specs)
- Lab Notes: 7 deep technical /lab-notes/ posts (Game of Life, Matrix Mode, Monitor, etc.)
- Updated: wiki/sources/dansanderson.com.md → index with one-line summary + link per article; Digest table is the complete 44 in blog order (newest first); Lab Notes in a separate section; hub + Welcome Guide as non-blog site sections
- Verified against the paginated blog at /mega65/ (4 pages = 12+12+12+8 = 44)

## 2026-06-10 | assets | official PDF library downloaded to raw/assets/

- Added: mega65-userguide.pdf (342pp), mega65-basic65-reference.pdf (345pp), mega65-developer-guide.pdf (351pp), mega65-chipset-reference.pdf (245pp), mega65-book.pdf (1455pp), MEGA65_BASIC_65_Referenzhandbuch_DE.pdf (334pp, German)
- Source: Filehost builds of 2026-04-08 (v1.2), per the Confluence Documentation Landing Page; German ref from 65site.de
- Created: raw/assets/README.md (index + refresh instructions)
- Updated: CLAUDE.md (books path now raw/assets/)

## 2026-06-10 | ingest | MEGA65-mega65-core | FPGA core (VHDL), release 0.97.2 — brief capture

- Created: wiki/sources/MEGA65-mega65-core.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/github/README.md, inbox.md

## 2026-06-10 | ingest | lgblgblgb-xemu | Xemu emulator — usage-level brief capture

- Created: wiki/sources/lgblgblgb-xemu.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/github/README.md, inbox.md

## 2026-06-10 | ingest | dansanderson-easyasm65 | on-device 45GS02 assembler; full manual in raw

- Created: wiki/sources/dansanderson-easyasm65.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/github/README.md, inbox.md

## 2026-06-10 | ingest | MEGA65-mega65-code-snippets | official meta-repo of community code/tools links

- Created: wiki/sources/MEGA65-mega65-code-snippets.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/github/README.md, inbox.md

## 2026-06-10 | ingest | MEGA65-mega65-tools | m65, mega65_ftp, etherload, coretool, romdiff CLI suite

- Created: wiki/sources/MEGA65-mega65-tools.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/github/README.md, inbox.md

## 2026-06-10 | ingest | RetroCogs-Mega65Tutorials | 15-step 45GS02/VIC-IV tutorial code curriculum

- Created: wiki/sources/RetroCogs-Mega65Tutorials.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/github/README.md, inbox.md

## 2026-06-10 | ingest | MEGA65-mega65-user-guide | LaTeX source of all 5 official books; full clone for greppable spec

- Created: wiki/sources/MEGA65-mega65-user-guide.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/github/README.md, inbox.md

## 2026-06-10 | ingest | c64-wiki.com | encyclopedia hardware-spec article (stub, some dated info)

- Created: wiki/sources/c64-wiki.com.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | ingest | mega65.atlassian.net | official Confluence wiki — structure, releases, how-tos

- Created: wiki/sources/mega65.atlassian.net.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | ingest | files.mega65.org | Filehost shell capture — official software repository pointer

- Created: wiki/sources/files.mega65.org.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | ingest | wiebow.mega65.com | complete Kick Assembler + c1541 + Xemu + etherload cross-dev pipeline

- Created: wiki/sources/wiebow.mega65.com.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | ingest | retrocogs.mega65.com | RetroCogs VIC-IV tutorials — screen layout, scrolling, FCM/NCM, RRB pixies

- Created: wiki/sources/retrocogs.mega65.com.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | ingest | retrocombs.com | retroCombs MEGA65 Resource Page + User's Guide video series index

- Created: wiki/sources/retrocombs.com.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | ingest | dansanderson.com | Dan Sanderson's MEGA65 hub — Welcome Guide (12 chapters), cross-development series, Digest

- Created: wiki/sources/dansanderson.com.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | ingest | mega65.org | official MEGA65 site — product overview, PDF manuals map, emulator guide, alternative cores

- Created: wiki/sources/mega65.org.md
- Updated: wiki/index.md, wiki/overview.md, wiki/log.md, raw/web/README.md, inbox.md

## 2026-06-10 | init | wiki scaffolded

- Created `.pin-llm-wiki.yml`
- Created `inbox.md`, `CLAUDE.md`, `raw/`, `wiki/`
