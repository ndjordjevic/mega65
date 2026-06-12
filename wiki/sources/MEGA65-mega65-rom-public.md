---
type: source
source_url: https://github.com/MEGA65/mega65-rom-public
tags: [mega65-rom, basic-65, kernal, changelog, version-history, closed-source, issue-tracker]
related: [MEGA65-mega65-user-guide, MEGA65-mega65-core, mega65.org, dansanderson.com, files.mega65.org]
product: mega65-rom-public
detail_level: standard
created: 2026-06-11
updated: 2026-06-11
---

The **public issue-tracker and CHANGELOG** for the MEGA65 ROM. The ROM itself (BASIC 65 + KERNAL) is **closed source** — licensed to MEGA65 owners, with private source access via Discord — so this repo isn't ROM code; its value is the canonical **version history**. The `CHANGELOG.md` is the authoritative answer to "which ROM version introduced feature X?", complementing the official BASIC 65 / Developer references in [[MEGA65-mega65-user-guide]].

_All claims below are sourced from ../../raw/github/MEGA65-mega65-rom-public.md unless otherwise noted._

## What it does

A public place to file ROM bugs, plus `CHANGELOG.md` tracking every BASIC 65 and KERNAL change. Note the ROM is proprietary (owner-licensed); only the issue tracker + changelog are public.

## CHANGELOG highlights

- Versions: **920287** (Release 0.9, Jan 2022) → newest beta **920421**; latest stable **920413 (v0.97, 2025-04-27)**.
- BASIC 65: `LOG2()`, `HASBIT()`, `RPT$()`, `RDISK()`; binary literals (`%1010`); wider bitwise ops; `CIRCLE`/`ELLIPSE` and `MEM` improvements.
- Graphics: hi-res sprite modes (920415).
- I/O: D64 image support, enhanced `MOUNT`, `DIR`/`TYPE` pattern matching.
- KERNAL: `CURSOR`, `SYSFLAGS`, `VERSIONQ`, `KEYSCAN`, 5-button `JOY()`, hardware `POT()`.
- Fixes: 920410 restored `INT()` to floor (trig regression); 920416 division rounding.

## When to use

When a BASIC 65 keyword or KERNAL routine depends on a minimum ROM version, or to see what changed between firmware releases. For the feature *documentation* (not version history), use [[MEGA65-mega65-user-guide]] (BASIC 65 Reference); download ROM binaries from [[files.mega65.org]].

## Ecosystem

The ROM is built against the hardware in [[MEGA65-mega65-core]]; [[dansanderson.com]] (whose author contributes to the ROM) links directly to this CHANGELOG. Release notes also surface on [[mega65.org]] and the Confluence wiki [[mega65.atlassian.net]].
