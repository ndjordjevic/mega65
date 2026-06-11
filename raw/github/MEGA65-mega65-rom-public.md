# MEGA65/mega65-rom-public

## Fetch log
- Inbox URL: https://github.com/MEGA65/mega65-rom-public
- Final URL: https://github.com/MEGA65/mega65-rom-public
- Fetched: 2026-06-11
- Mode: standard (brief GitHub capture — README + CHANGELOG)

## What it is

The **public issue-tracker and CHANGELOG** for the MEGA65 ROM. Important: this repo does **not** contain the ROM source — the ROM (BASIC 65 + KERNAL) is **closed source**. The README states: "This repository is for reporting issues with mega65-rom (the closed ROM)." As a MEGA65 owner you hold a license to the ROM; licensed owners can request access to the private source repo via Discord.

So the captured value here is two things:
1. A place to file/track ROM bugs (29+ open issues, 46+ commits).
2. **`CHANGELOG.md`** — the authoritative version history of BASIC 65 and the KERNAL. (Dan Sanderson's site links directly to this CHANGELOG.)

## CHANGELOG highlights

- Versions documented: **920287** (Release 0.9, Jan 2022) → newest beta **920421**. Latest stable: **ROM 920413 (v0.97, 2025-04-27)**.
- **BASIC 65 features added over time:** `LOG2()`, `HASBIT()`, `RPT$()`, `RDISK()`; binary literals (`%1010`); wider-range bitwise operators; `CIRCLE`/`ELLIPSE` improvements; upgraded `MEM` screen-memory allocation.
- **Graphics/sprites:** high-resolution sprite modes (920415), enhanced screen memory.
- **I/O & storage:** D64 disk-image support, enhanced `MOUNT`, better disk error handling, `DIR`/`TYPE` pattern matching.
- **KERNAL routines:** new official APIs `CURSOR`, `SYSFLAGS`, `VERSIONQ`; `KEYSCAN`; `JOY()` with 5-button controllers; `POT()` using MEGA65 hardware registers.
- **Bug-fix examples:** 920410 restored `INT()` to a true floor function (fixed trig regressions); 920416 corrected division rounding.

## Why it matters

This CHANGELOG is the canonical answer to "which ROM version introduced feature X?" — useful when a BASIC 65 keyword or KERNAL routine in the official docs depends on a minimum ROM version.

## Links
- Repo / issues: https://github.com/MEGA65/mega65-rom-public
- CHANGELOG: https://github.com/MEGA65/mega65-rom-public/blob/main/CHANGELOG.md
