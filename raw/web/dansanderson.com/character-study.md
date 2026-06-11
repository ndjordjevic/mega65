# Character Study

- URL: https://dansanderson.com/mega65/character-study/
- Published: May 30, 2025
- Fetched: 2026-06-11

## Overview

Character graphics fundamentals: screen memory organization, color memory, resolution modes, and the memory efficiency rationale behind character-based display.

## Memory Organization

- Screen grid: 80×25 = 2,000 bytes; each cell references one of 256 character patterns.
- **SCRNPTR** ($D060–$D063): controls which memory address the VIC reads. Switch screens instantly by updating this register.
- Color memory: 32 KB at $FF8.0000–$FF8.7FFF. Each byte: 5 color-selection bits + 3 attribute bits (blink, reverse, underline).
- 32-color palette; each entry = 12-bit RGB.

## Resolution Modes

VIC-IV supports:
- 320px (40-column) or 640px (80-column) horizontal
- 200px (25-row) or 400px (50-row) vertical

## Key Commands

- `T@&(col, row) = screencode` — plot character at coordinates
- `C@&(col, row) = color` — set color at coordinates
- `SCRNPTR` register — switch display pages for animation

## Community Updates (at time of issue)

- MEGA65 platform v0.97 released after 14 months of development
- C64 core v5.2 addresses HDMI display bugs
- M65Connect v2.4 improves macOS compatibility
- Screenful of BASIC 2025 compo concluded with 26 entries
