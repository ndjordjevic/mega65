# Game of Life on the MEGA65, in Assembly Language

- URL: https://dansanderson.com/lab-notes/mega65-game-of-life-in-assembly/
- Published: July 23, 2022
- Fetched: 2026-06-11

## Overview

Implementing Conway's Game of Life in 45GS02 assembly using ACME assembler. Achieves ~100 generations/second vs BASIC's 3.04 seconds/generation (300× faster).

## Assembler: ACME

Chosen for strong MEGA65 support and traditional syntax. Kick Assembler popular for larger projects; cc65 nearly ready but not fully polished.

## BASIC Starter Structure

All PRGs start at $2001; machine code starts at $2014 (after canonical BASIC one-liner):
```
10 BANK 0:SYS $2014
```

## Key Techniques

**Line buffer management**: two 80-byte buffers (previous/current row). `bufsel` byte tracks active buffer; swap via XOR:
```assembly
lda bufsel
eor #1
sta bufsel
```

**Zero page indirect indexing**: base page $16 for rapid memory access.

**16-bit arithmetic with carry**:
```assembly
lda cell_ptr
adc #80
sta cell_ptr
bcc +
inc cell_ptr+1
+
```

**Relative branch labels**: `-` and `+` for local loops.

## Cell Processing

Screen traversal: 23 rows × 78 columns; cell pointer (`cell_ptr`) at zero page $FB–$FC.

Game of Life rule condensed: "a cell lives if it has exactly 3 neighbors, or 2 neighbors AND was already alive."

## Debugging Techniques

- Write test values to screen memory for visual inspection
- Use `brk` to invoke monitor mid-execution
- Increment border/background colors as execution markers
- Custom `debug_waitkey` for pausing at checkpoints

## Performance

- BASIC: ~3.04 seconds/generation
- Assembly: ~0.01 seconds/generation (~300× faster)

## Downloads

- `golml.a`: ACME assembler source
- `golml.prg`: Pre-assembled executable
