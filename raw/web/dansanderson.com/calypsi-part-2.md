# Calypsi C, part 2: Using memory

- URL: https://dansanderson.com/mega65/calypsi-part-2/
- Published: July 15, 2026
- Fetched: 2026-07-16

## Overview

Continues the Calypsi C series (following [calypsi-part-1](calypsi-part-1.md)), tackling advanced memory management needed to compile programs beyond the standard 32 KB PRG limit — worked through the ongoing port of Unix *Rogue* (see [classic-rogue](classic-rogue.md)) to the MEGA65.

## Memory architecture constraints

- MEGA65 has 384 KB main memory but a 16-bit address space mapped onto a 28-bit physical space.
- Default `DLOAD` supports only 53 KB PRG files; usable code space is further capped at ~40 KB by KERNAL ROM shadowing at $C000–$FFFF.
- Calypsi's default linker configuration restricts programs to 32 KB ($2001–$9FFF).

## Far pointers and far variables

- `__far` qualifier gives 32-bit pointer access to upper memory: `uint8_t __far *colormem = 0xff80000;` reaches physical $FF8.0000.
- `__huge` pointers allow cross-bank pointer arithmetic without the restrictions of `__far`.
- Parser bug workaround: use `__attribute__((far))` instead of `__far` in some contexts.

## Memory configuration (`.scm` linker files)

The Calypsi linker config is written in Scheme:
- **Memories** — named address ranges tagged by usage type (`program`, `zeroPage`, `stackPage`, `freeSpace`).
- **Sections** — logical code/data groupings (`code`, `data`, `zdata`, `cdata`).
- **Fragments** — individual allocations from compiled objects.
- **Placement groups** — subdivide a single address range across multiple memory types.

Heap example:
```scheme
(block heap (size #x2000))
(memory bss_main_lo (address (#xa000 . #xbfff))
  (section (heap #xa000)))
```

## Multi-region strategy (for the Rogue port, ~86 KB total)

Code spread across five 24 KB regions switched via the **MAP register**:
- Region 0: $2200–$7FFF (game loop entry point)
- Regions 1–3: $2000–$7FFF via MAPLO offset
- Region 4: 8 KB remainder
- Common region: $1600–$1EFF (MAP-switching code, must stay resident across switches)

Section assignment via pragma:
```c
#pragma clang section text="r1Text" data="r1Data" rodata="r1Rodata" bss="r1Bss"
```

Raw multi-file output instead of a single PRG:
```
ld6502 ... -o crogue-common.raw --raw-multiple-memories \
  --no-merge-raw-memories --output-format=raw
```
Produces `crogue-common.raw`, `crogue-r0.raw`, `crogue-r1.raw`, etc., each `BLOAD`ed separately.

## Code size optimization

- `printf()`: full float-formatting build 10,983 bytes; integer-only (`%d %s %c %%`) 3,708 bytes; plain `puts()` 2,761 bytes. Calypsi auto-selects the leanest variant actually used; force with `--rtattr printf=nofloat`.
- Programs that never return to BASIC save 87 bytes via `--rtattr exit=simplified`.
- Rogue-specific trims: removed Unix-only code, simplified screen I/O, cut large ASCII-art strings (482 bytes from `rip.c`), disabled the high-score file — brought the build from 112 KB down to ~86 KB.

## Boot loader pattern

BASIC loader `BLOAD`s each region then jumps to the entry point, saved as `AUTOBOOT.C65` on the D81 for automatic loading:
```basic
10 PRINT "LOADING ROGUE..."
20 BLOAD "CROGUE-COMMON",P($01600),R
30 BLOAD "CROGUE-R0",P($02200),R
...
80 SYS $220D
```

## Linker report analysis

Calypsi emits `.lst` allocation reports: memory-utilization percentages, section placement, fragment counts, and unused space per region — used to verify the memory config is laid out correctly.

## Related resources & links

- **MEGASPUTM** — exemplar multi-region Calypsi project (a graphic-adventure engine): https://codeberg.org/kibo/megasputm
- VICE's `cc1541` tool, used for D81 disk-image creation.
- VSCode C-language workaround for the `__far` keyword.
- "Colour Memory" section of the MEGA65 Compendium; Calypsi manual §6.1 (Sections) and §18.6 (Library optimization).
- Original Unix Rogue source (C, curses library).
- New MEGA65 cores mentioned in passing: Amiga 500 core by sy2002 (https://sy2002.github.io/AExp), Commodore 128 core by Stefan Eilers (https://github.com/eilers/c128Mega65).

## Next

Part 3 will cover inter-region function calls with automatic MAP-register switching on call/return — flagged as "a doozy."
