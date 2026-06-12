---
type: source
source_url: https://github.com/RetroCogs/Mega65Tutorials
tags: [45gs02-assembly, vic-iv-tutorials, rrb-pixies, fcm-ncm, kick-assembler, software-sprites, parallax]
related: [retrocogs.mega65.com, wiebow.mega65.com, MEGA65-mega65-code-snippets, MEGA65-mega65-user-guide]
product: retrocogs
detail_level: standard
created: 2026-06-10
updated: 2026-06-12
---

The companion code repo to [[retrocogs.mega65.com]] — a 15-step graduated curriculum of working 45GS02 assembly programs for VIC-IV graphics programming, from a blank skeleton to advanced software-sprite ("pixie") engines. Each numbered tutorial pairs with a blog post; together they are the most complete hands-on course for MEGA65 graphics coding.

**Full clone at `raw/github/RetroCogs-Mega65Tutorials/`** — all `.asm` files, `mega65system.asm`/`mega65macros.asm` library, and asset binaries are directly readable and greppable.

_All claims below are sourced from `raw/github/RetroCogs-Mega65Tutorials/` unless otherwise noted._

## What it does

Progression: program skeletons (tutorial_0) → screen layout (1) → text entry (1b) → scrolling (2) → Full Color Mode (3, 3a with RRB) → Nibble Color Mode (4) → RRB scrolling (5) → RRB parallax (6) → RRB objects (7) → advanced pixies (8, 9, 10 flip-pixies).

## Key features

- `mega65system.asm` and `mega65macros.asm` — reusable system-setup and macro library shared by all tutorials; a useful starting point for any new MEGA65 assembly project.
- Asset pipeline included: PNG sources with pre-converted `_chr.bin` (character data) and `_pal.bin` (palette) binaries for FCM and NCM modes.
- Kick Assembler syntax throughout; makefile-driven build; Xemu launch with `-uartmon :4510` enabling monitor-based debugging.

## Architecture

Single flat repo, one self-contained .asm per concept, all including the shared system files — read in numeric order. The RRB-based tutorials (3a, 5–10) build the case that RRB pixies can replace hardware sprites for layered, sprite-heavy games.

## Installation

Clone, assemble with Kick Assembler (45GS02 fork — see [[wiebow.mega65.com]] for the toolchain), run in Xemu or on hardware.

## Example usage

Start with `tutorial_1_screens.asm` alongside the "VIC-IV Screen Layout" blog post; the makefile shows the assemble-and-launch loop.

## Maintenance status

12 stars, active (pushed 2025-12), no license declared, no releases — consume at HEAD.

## Ecosystem

Documented by [[retrocogs.mega65.com]]; complements the official spec in [[MEGA65-mega65-user-guide]] (register authority) with executable examples.
