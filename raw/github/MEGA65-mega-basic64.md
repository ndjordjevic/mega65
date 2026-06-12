# MEGA65/mega-basic64

## Metadata
- Stars: 13
- Primary language: Assembly
- Default branch: master
- Latest release: none
- License: none
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/mega-basic64

## Description
Experimental MEGA65 extensions to C64 BASIC 2

## README
MEGA65 Extended BASIC — an experimental extension to C64 BASIC 2 providing a testbed for MEGA65-specific 256-colour text mode graphics and 16-colour sprite capabilities. Not a finished product; started as a development tool for the MEGA65 team.

**New commands (selection):**
- `FAST` / `SLOW` — CPU speed control
- `COLOUR TEXT/BORDER/SCREEN <0-255>` — colour selection (16 colours; upper 4 bits = VIC-III attributes: BLINK, UNDERLINE, REVERSE, BOLD)
- `COLOUR SPRITE <n> COLOUR <idx> = <r>,<g>,<b>` — per-sprite RGB colour
- `TILE SET LOAD "<filename>"` — load tile set + canvases into graphics memory
- `CANVAS <0-255> NEW <w>,<h>` / `DELETE` / `CLR` / `STAMP ... ON CANVAS ... AT <x>,<y>` / `SET TILE <x>,<y> = <n>` — canvas management and tile composition

**Memory layout:** C65 DOS in Bank 1 leaves 56 KB (54 KB usable); CANVAS 0 is 80×50, requiring 8000 bytes for off-screen buffer hidden under C64 KERNAL. Another 8000 bytes under C64 BASIC ROM for compositing. 8000 bytes colour RAM for CANVAS 0. VIC-IV set to 40×25–80×50 virtual row 80, 16-bit colour, screen RAM at $A000–$BFFF.

**Rendering:** Raster IRQ composites C64 screen ($0400) on top of CANVAS 0, meaning BASIC text and tile graphics coexist. POKE to $0400 updates next frame.

**Status:** Very old (last commit 2019), no license, likely superseded by later MEGA65 development. Useful as a historical reference for early MEGA65 graphics architecture exploration.

## Top-level structure
- dir src/ — BASIC extension assembly sources
- dir assets/ — tile/graphics data
- file Makefile — build system
- file README.md, test, testbas, testn4 — tests and README
