# Calypsi C, part 3: Making Large Programs

- URL: https://dansanderson.com/mega65/calypsi-part-3/
- Published: August 29, 2026
- Fetched: 2026-08-30

## Overview

Third installment of the Calypsi C series (follows [calypsi-part-1](calypsi-part-1.md)
and [calypsi-part-2](calypsi-part-2.md)), continuing the port of Unix *Rogue*
(see [classic-rogue](classic-rogue.md)) to the MEGA65. Topic: **inter-region
function calls** — dispatching calls between code that lives in different 24 KB
memory regions, with automatic MAP-register switching on call and return.

## Memory model recap

- 16-bit CPU window: $2000–$7FFF (MAPLO-mapped) + $E000–$FFFF (MAPHI, normally KERNAL).
- Five 24 KB **regions** in the 28-bit physical space, selected via MAP switching.
- **Common area** $1600–$1FFF: always resident, interrupt-safe; holds the dispatcher
  and any data shared across regions (space-constrained).
- `.scm` linker config defines section placement and per-region MAP offsets.

## MAP register mechanics

Region switch sequence (interrupts must be disabled across `map`/`eom`):
```asm
lda #$80
ldx #$e0
ldy #$00
ldz #$83
map
eom
```

## Calypsi integration

Per-region section assignment via pragma:
```c
#pragma clang section text="r2Text" data="r2Data" rodata="r2Rodata" bss="r2Bss"
```

Compiler flags that matter for multi-region builds:
- `--no-cross-call` — stop the linker sharing/reusing code across regions
  (fix identified by *kibo* after multi-day debugging).
- `--no-interprocedural-cross-jump` — disable inter-region jump optimization.

`__far` qualifier still used to reach variables in upper physical memory.

## Region-dispatch mechanism

`dispatch.h`:
```c
void region_dispatch();
extern volatile uint16_t region_dispatch_dest_maplo;
extern void (*region_dispatch_dest_addr)(void);

#define REGION_0 0xe000
#define REGION_1 0xe080
#define REGION_2 0xe100
#define REGION_3 0xe160
#define REGION_4 0xe1c0

#define REGION_DISPATCH(dest_maplo, func, ...) \
  ({                                            \
    region_dispatch_dest_maplo = dest_maplo;    \
    region_dispatch_dest_addr = (void (*)(void))func; \
    ((__typeof__(&(func)))region_dispatch)(__VA_ARGS__); \
  })
```

Call site:
```c
int result = REGION_DISPATCH(REGION_2, times, 7, 3);
```

Assembly implementation (`dispatch.s`), in the common section:
- Stashes CPU registers (A/X/Y/Z) with `stq`.
- Keeps a 32-byte stack of caller MAPLO values → supports 16 nested cross-region calls.
- Sets destination MAPLO before `jsr`, restores caller MAPLO after `rts`;
  tracks state in `region_dispatch_last_maplo`.

Exposing an assembly symbol to C:
```asm
.public region_dispatch
.section commonText, text, root
region_dispatch:
  ; ...
  rts
```

Inline-assembly constraint syntax (Calypsi):
```c
__asm(
  " inx\n"
  " txa\n"
  : "=Ka" (out)
  : "Kx" (xx)
  : "a", "x"
);
```
`"=Ka"` = output via accumulator; `"Kx"` = input via X; clobber list `"a","x"`.
Zero-page scratch types `zp8` / `zp16` / `zp32`, referenced as `%0`, `%1`, …

## Rogue port status

- ~90 KB program now compiles across **two** banks; dungeon is walkable, item
  pickup works; cross-region visibility bugs remain.
- 23,674 bytes of global data forced a custom visibility strategy.
- Nearly every cross-module call became a cross-region dispatch; passing string
  literals needed a specialized string-dispatch macro.
- **Author abandons the "dirty port"** and pivots to a purpose-built game shell:
  ~384 KB fast RAM, C interrupt handlers, switchable major modes each with their
  own memory map, KERNAL-active disk mode with Attic-RAM stashing, game-state
  persistence, ROM banks 2–3 repurposed for graphics.

## Documented limitations

- No direct cross-region data access — need accessor functions or dispatch.
- Shared data must sit in the small common area.
- Pointer dereference requires the target region be mapped in.
- String literals in dispatched calls must be pre-buffered.
- Debugger breakpoints are ambiguous across regions; dispatch overhead frustrates optimization.

## Links & resources

- Calypsi 5.18: https://github.com/hth313/Calypsi-tool-chains/releases/tag/5.18
  (improvements by author hth313 based on series feedback).
- Calypsi manual ch. 20 (Assembly interface), ch. 21 (Assembler).
- MEGA65 alternate cores: https://cores.mega65.org/
- VCF Midwest: September 12–13, Schaumburg, IL — https://vcfmw.org/
- EU packaging regulation (European Commission site; Heise article) — mentioned in passing.

## Next

September Digest promised to be "more laid-back"; game-shell framework is the new
direction, with source to be released if the game is finished.
