# robotfindskitten, part 2

- URL: https://dansanderson.com/mega65/robot-finds-kitten-2/
- Published: November 13, 2023
- Fetched: 2026-06-11

## Overview

Assembly language implementation of robotfindskitten: KERNAL API, screen memory access, color memory, and 45GS02 addressing modes.

## Key KERNAL Routines

| Routine | Address | Purpose |
|---|---|---|
| `chrout` | $FFD2 | print PETSCII code in A |
| `primm` | $FF7D | print null-terminated string embedded in code |
| `plot` | $FFF0 | carry clear: set cursor (X=col,Y=row); carry set: get cursor |

## Screen Memory Access

- 80×25 text mode: 2,000 bytes, row-major (80 bytes/row)
- SCRNPTR at $D060–$D063
- Coordinate → address: `addr = SCRNPTR_base + row * 80 + col` (use bit-shifting for ×80)
- **Self-modifying code** to write arbitrary addresses into instructions
- Color memory: expose full 2 KB with CRAM2K register ($D030)

## Addressing Modes

- Base page indirect: store 16-bit address in base page; `lda (ptr),y`
- 32-bit base page indirect (MEGA65 extension): access upper memory without workarounds
- B register designates active base page; KERNAL requires B = $00

## Code Patterns

Print null-terminated message with `primm`:
```assembly
jsr $FF7D
!pet "HELLO",0
; code continues here
```

Plot char at coordinate (self-modifying pattern):
```assembly
ldy row
lda #0
jsr multiply_by_80  ; result in A/X
clc
adc #col
; store to SCRNPTR-relative address
```

## Next Steps

Part 3 covers: keyboard input, hardware random number generator ($D7EF), timing via CIA/VIC, and parallel array data structures for item descriptions.
