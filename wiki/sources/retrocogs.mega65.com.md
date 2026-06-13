---
type: source
source_url: https://retrocogs.mega65.com/
tags: [vic-iv, raster-rewrite-buffer, fcm-ncm, seam, software-sprites, pixies, screen-layout, scrolling, hardware-registers, kick-assembler]
related: [dansanderson.com, wiebow.mega65.com, RetroCogs-Mega65Tutorials, m-e-g-a.org]
product: retrocogs
detail_level: standard
created: 2026-06-10
updated: 2026-06-11
---

RetroCogs' "Coding for the Mega65" blog — register-level VIC-IV graphics tutorials, written by a developer building a shoot-'em-up (**FirstShot**) on the platform. Each tutorial pairs with working 45GS02 / Kick Assembler code in the companion repo [[RetroCogs-Mega65Tutorials]] (ingested separately). Where [[dansanderson.com]] teaches concepts and workflow, this source nails down the **exact hardware registers and bit layouts**. Small (5 posts) but unique as the prose reference for the tutorial code; revived in 2025 with the SEAM/FCM/NCM/RRB material.

**How to use this page:** the table is an index — each row links to a raw page under `../../raw/web/retrocogs.mega65.com/`. Unlike most web sources in this wiki, these raw pages are **near-verbatim captures** (full register details and code), not condensed summaries — the author intends them as a living reference. The `- URL:` at the top of each raw page is the original. Answer chain: this index → raw page → original URL.

_All claims below are sourced from ../../raw/web/retrocogs.mega65.com/ unless otherwise noted._

---

## Posts (all 5, newest first)

| Date | Article | Summary |
|---|---|---|
| 2025-08-14 | [rrb-for-pixies.md](../../raw/web/retrocogs.mega65.com/rrb-for-pixies.md) | Raster Rewrite Buffer for software sprites: GOTOX char (color RAM byte0 bit4), the per-row SCREEN/COLOR data structure, transparency, char data layout (64-byte align), Y-offset (`fcm_yoffs`) + rowmask for arbitrary vertical placement, full 16×8 pixie offset table. Code included. |
| 2025-08-13 | [fcm-and-ncm.md](../../raw/web/retrocogs.mega65.com/fcm-and-ncm.md) | Setting up Full Color / Nibble Color Mode: C64 graphics refresher, SEAM (CHR16, $D054 bit0) and all the features it unlocks, the 4×256 palette system ($D070 MAPEDPAL/BTPALSEL/etc., $D100-D3FF, nibble-swap caveat), enabling FCM/NCM (ATTR $D031 bit5, FCLRHI $D054 bit2). Code included. ("In progress") |
| 2022-10-04 | [scrolling-the-vic-iv-screen.md](../../raw/web/retrocogs.mega65.com/scrolling-the-vic-iv-screen.md) | Smooth scrolling in all directions: oversized buffers, SCRNPTR ($D060/61) and COLPTR (offset from $FF80000), LINESTEP > CHRCOUNT, per-frame TEXTXPOS/TEXTYPOS shift + pointer increment formulas, vertical limits. Companion `tutorial_2_scrolling.asm`. |
| 2022-09-20 | [vic-iv-screen-layout.md](../../raw/web/retrocogs.mega65.com/vic-iv-screen-layout.md) | Custom screen sizes up to 720×576: CHRCOUNT/DISPROWS/LINESTEP, H640/H320 & V400/V200 scaling (and the ×2 register-unit gotcha), centering formulas for TEXTXPOS/TEXTYPOS/SDBDRWD/TBDRPOS/BBDRPOS. Companion `tutorial_1_screens.asm`. |
| 2022-09-12 | [welcome.md](../../raw/web/retrocogs.mega65.com/welcome.md) | Intro post — the FirstShot game project and why the blog exists. No technical content. |

---

## When to use

The go-to source when writing **VIC-IV graphics code**: setting up a custom screen size, smooth scrolling, full-color / nibble-color characters, or an RRB-based software-sprite engine — and you want the exact register names, bits, and addresses. Read alongside the official Chipset Reference ([[MEGA65-mega65-user-guide]]) for register authority and [[RetroCogs-Mega65Tutorials]] for the runnable code. For a gentler, more conceptual take on the same modes, see [[dansanderson.com]] (raster-rewrite-buffer, every-pixel-a-color, super-extended-attribute-mode).

## Ecosystem

Companion code at [[RetroCogs-Mega65Tutorials]] (github.com/RetroCogs/Mega65Tutorials); hosted on the community mega65.com subdomain family (like [[wiebow.mega65.com]]). The author's game project FirstShot motivates the tutorials. Code samples use Kick Assembler syntax (`.var`, `.for`, `.byte`).
