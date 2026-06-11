# Disassembling Crossroads, part 1

- URL: https://dansanderson.com/mega65/crossroads-part-1/
- Published: November 15, 2024
- Fetched: 2026-06-11

## Overview

Reverse engineering the classic C64 game *Crossroads* (Compute!'s Gazette, December 1987) using Retro Debugger. Introduces debugging techniques transferable to MEGA65 development.

## Key Technical Discoveries

- Custom character set at $2000; creatures animate through multiple tile definitions.
- "Spar" item animates by continuously updating a single tile definition.
- **Half-step movement**: creatures occupy two adjacent character cells during tile transitions.
- Sprite graphics for explosion animations; random sprite patterns generated during gameplay.
- Program loads at $0801 with BASIC bootstrap `10 SYS2300` → machine code at $08FC.

## Using Retro Debugger

Retro Debugger: a C64 emulator with real-time memory visualization. Key features:
- Real-time hex and assembly inspection
- Character set visualization (tiles animate live)
- Memory monitoring: filter for changed values to locate variables
- Found player lives counter at memory address $0011 by filtering for changes

## VIC Memory Bank

Character set at $2000 via VIC register $D018.

## Practical Session

1. Load game in Retro Debugger
2. Memory Monitor → filter for "decreased" values while losing a life
3. Identified $0011 = lives counter; modified to 99 to verify

## Next Steps

Part 2 will use Ghidra for complete human-readable assembly disassembly.
