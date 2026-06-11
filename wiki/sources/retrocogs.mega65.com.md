---
type: source
source_url: https://retrocogs.mega65.com/
tags: [vic-iv, raster-rewrite-buffer, fcm-ncm, hardware-registers, screen-layout, scrolling, software-sprites, kick-assembler]
related: [dansanderson.com, wiebow.mega65.com, RetroCogs-Mega65Tutorials]
product: retrocogs
detail_level: standard
created: 2026-06-10
updated: 2026-06-10
---

RetroCogs' "Coding for the Mega65" blog — the deepest publicly available VIC-IV graphics-programming tutorials, written by a developer building a shoot-'em-up (FirstShot) on the platform. Each tutorial pairs with working 45GS02 assembly in the companion repo github.com/RetroCogs/Mega65Tutorials (ingested separately in this wiki). Where [[dansanderson.com]] teaches workflow, this source teaches the hardware registers.

_All claims below are sourced from ../../raw/web/retrocogs.mega65.com.md unless otherwise noted._

## What it does

Register-level tutorials on VIC-IV graphics: screen layout, scrolling, Full Color Mode (FCM) / Nibble Color Mode (NCM) setup, and the Raster Rewrite Buffer (RRB) for software sprites ("pixies").

## Key features

- **Screen layout**: the VIC-IV supports arbitrary screen sizes up to 720×576 (PAL) / 720×480 (NTSC). Layout is driven by CHRCOUNT (chars per row; values >255 currently buggy in VHDL), DISPROWS (rows drawn), and LINESTEP (bytes to advance per row — enables logical screens wider than the display). Covered in `tutorial_1_screens.asm`.
- **Scaling modes**: H640 (boot default, 80 columns) vs H320 (clear bit 7 of $D031) — layout registers (TEXTXPOS, SDBDRWDLSB/MSB at $D05C/D) are always in H640 units, so H320 pixels count double; V400 vs V200 (bit 3 of $D031) similarly — TEXTYPOS, TBDRPOS, BBDRPOS are in V400 units. Centering formula: LeftEdge = 400 − PixelsWide/2 with both TEXTXPOS and SDBDRWD set to it.
- **Raster Rewrite Buffer**: a 2048-pixel-wide single-line buffer that overlays extra characters on already-drawn ones — multiple background layers or software sprites without hardware sprite limits. Within a row, a GOTOX character (bit 4 of color-RAM byte 0) arbitrarily resets the horizontal draw position; each row's screen data becomes: GOTOX 0 → background chars → GOTOX x → pixie char → end-of-line GOTOX 320.
- **SEAM (Super Extended Attribute Mode)**: each character occupies two bytes in both screen RAM and color RAM — the prerequisite layout for RRB and NCM work.
- Code samples are written for Kick Assembler (`.var`, `.for`, `.byte` macro syntax).

## Architecture and concepts

The blog's framing: MEGA65 graphics are an extension of C64 concepts, so each tutorial starts with the C64 baseline and shows what the VIC-IV adds. The register tables in the posts map names (CHRCOUNT, LINESTEP, TEXTXPOS…) to $D0xx addresses.

## Main APIs

Key registers: $D031 (H640/V400 mode bits), $D05C/D (side-border width), TEXTXPOS/TEXTYPOS, TBDRPOS/BBDRPOS, CHRCOUNT/DISPROWS/LINESTEP. Tutorial posts: the-vic-iv-screen-layout (2022-09), scrolling-the-vic-iv-screen (2022-10), vic-iv-graphics-setting-up-fcm-and-ncm (2025-08, in progress), vic-iv-graphics-using-rrb-for-pixies (2025-08).

## When to use

The go-to source when writing VIC-IV graphics code: setting up a custom screen size, scrolling, full-color/nibble-color characters, or RRB-based sprite engines. Read alongside the official Chipset Reference for register authority.

## Ecosystem

Companion code at github.com/RetroCogs/Mega65Tutorials; hosted on the community's mega65.com subdomain family (like wiebow's blog). The author's game project FirstShot motivates the tutorials.
