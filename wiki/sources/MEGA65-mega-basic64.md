---
type: source
source_url: https://github.com/MEGA65/mega-basic64
tags: [basic-extension, c64-basic-2, 256-colour-text, tile-graphics, canvas-system, vic-iv, experimental]
related: [MEGA65-mega65-core, MEGA65-open-roms]
product: mega-basic64
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**mega-basic64** is an experimental extension to C64 BASIC 2 that adds MEGA65-specific 256-colour text mode graphics and sprite/canvas commands. It was an early MEGA65 team testbed for exploring MEGA65 graphics capabilities from a high-level BASIC interface — not a shipping product, and largely superseded by later MEGA65 BASIC 65 development.

_All claims below are sourced from ../../raw/github/MEGA65-mega-basic64.md unless otherwise noted._

## What it does

Extends C64 BASIC 2 with canvas and tile graphics commands: `FAST`/`SLOW`, `COLOUR TEXT/BORDER/SCREEN`, `COLOUR SPRITE`, `TILE SET LOAD`, `CANVAS NEW/DELETE/CLR/STAMP/SET TILE`. The VIC-IV is configured for an 80×50 virtual screen with 16-bit colour. A raster IRQ composites C64 `$0400` text over CANVAS 0, letting BASIC programs freely mix text output and tile graphics.

Memory layout: CANVAS 0 buffer at 8000 bytes under C64 KERNAL; colour RAM buffers; 54 KB free for graphics. The system reserves off-screen buffer space for compositing but leaves the BASIC program area intact.

## Maintenance status

13 stars, 4 forks, no license, last pushed 2019-01-20. Archived/stale. Historical interest: shows the tile/canvas graphics system design that influenced later MEGA65 VIC-IV feature development. Useful as a reference for understanding the MEGA65's early graphics architecture experiments.
