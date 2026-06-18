# Classic Rogue

- URL: https://dansanderson.com/mega65/classic-rogue/
- Published: June 16, 2026
- Fetched: 2026-06-18

## Overview

A deep dive into the classic 1980s dungeon-crawler *Rogue* — its design and C source architecture — followed by an attempt to port the original Unix source to the MEGA65 with the Calypsi C compiler. The original compiles, but the resulting build needs ~112 KB, well beyond Calypsi's default 31 KB linker limit, so the port becomes a memory-budgeting problem rather than a simple recompile.

## The game

**Rogue: Exploring the Dungeons of Doom** (Toy, Wichman, Arnold; early 1980s) — the seminal procedurally-generated dungeon crawler that named the "roguelike" genre. Defining traits: procedural level generation, turn-based movement, and permadeath. Source released under a BSD license in 1986.

Rogue-descended games still in active development include **NetHack** (1987) and **Angband** (1990).

## Rogue's architecture (the technical content)

- **Game loop:** `main()` → `playit()` → repeated `command()` calls.
- **Memory model:** global variables + local stack + dynamic heap allocation.
- **Daemon/fuse system:** time-based effects implemented with function pointers and pooled data structures (daemons run every turn, fuses fire after a countdown).
- **Display:** built on the Unix **curses** library (windows, cursor ops, character I/O). The screen itself is the source of truth — the game *reads characters back from the display* for collision detection rather than keeping a separate map model.
- **Conditional compilation:** features such as wizard (debug) mode gated behind compile flags and a password.

## Porting to the MEGA65

- Compiled with the **Calypsi C** MEGA65-native toolchain.
- Original Unix source compiles successfully, but the MEGA65 build measures **~112 KB** vs. the **31 KB** Calypsi default linker limit — the central obstacle to a working port.

## Related MEGA65 / FPGA work

- **Roguecraft DX** (Badger Punch Games) — a "clear descendant of the seminal Unix game," available for MEGA65, Amiga, Game Boy Color, and modern PC. (The same game Dan used to introduce RRB in the [raster-rewrite-buffer](raster-rewrite-buffer.md) post.)
- **MiSTer2MEGA65 Porting Guide** (MJoergen & sy2002) — framework documentation for porting FPGA cores to the MEGA65.

## Reference materials & links

- David Silva's modern Rogue build: https://github.com/Davidslv/rogue (BSD-licensed C source).
- Original BSD Rogue source (1986).
- Roguelike Celebration YouTube channel (ten years of archived talks).
- Vintage Computer Festival photo album from the May 2026 event.
