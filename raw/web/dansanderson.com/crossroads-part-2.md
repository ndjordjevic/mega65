# Disassembling Crossroads, part 2

- URL: https://dansanderson.com/mega65/crossroads-part-2/
- Published: January 31, 2025
- Fetched: 2026-06-11

## Overview

Deep technical disassembly of *Crossroads* using Ghidra (v11.2.1). Covers Ghidra setup for C64, key program structure discoveries, and future MEGA65 Ghidra tooling plans.

## Ghidra Setup for C64

1. Import crossroads.prg as raw binary; configure memory map to align with C64 address space ($0801 start).
2. Create overlays for I/O registers ($D000–$DFFF) and KERNAL ROM ($E000–$FFFF).
3. Import symbol files (IO.txt, KERNAL.txt, RAM.txt) to auto-label hardware registers and system routines.

Symbol files and overlays downloadable from the article.

## Key Discoveries

**Program Structure**:
- BASIC bootstrap calls machine code at $08FC (2300 decimal)
- IRQ interrupt handler at $11C4 drives the game loop

**Graphics Init Routine**:
- Copies PETSCII char data from ROM ($D000) to RAM ($2000)
- Transforms right-facing sprites into left/up/down orientations via flipping + rotation
- Creates half-tile animation frames via bit-shifting
- Sets custom char memory via VIC register $D018

**No KERNAL usage**: avoids jump table calls entirely; no KERNAL vectors used.

**Self-modifying code**: limited instances, primarily utility subroutines modifying their own addressing operands.

**Memory Layout**:
- $080D–$08FB: graphics tile data (16-byte animation frames per creature)
- $0CAC–$0DC4: screen layout text and static display data

## Methodology Note

"Ghidra is not magic — it identifies patterns but requires operator expertise to distinguish code from data and recognize hardware-specific memory usage."

## Future MEGA65 Ghidra Tooling

Planned: 45GS02 CPU processor definition (SLEIGH language), MEGA65 hardware register symbols, bitfield visualization, and re-assemblable source export.
