# Using the MEGA65 Monitor to Troubleshoot Assembly Programs

- URL: https://dansanderson.com/lab-notes/mega65-monitor/
- Published: July 26, 2022
- Fetched: 2026-06-11

## Overview

The MEGA65 built-in machine language monitor: commands, number formats, register display, memory editing, assembly/disassembly, BRK-based debugging, and the Freeze monitor.

## Three Monitors on MEGA65

1. MEGA65 monitor (runs as regular program; enter with `MONITOR`)
2. Freeze monitor (accessible via Freeze menu; limited commands)
3. Matrix Mode debugger (runs alongside active programs)

## Number Formats

| Prefix | Meaning |
|---|---|
| (none) | Hexadecimal |
| `$` | Hexadecimal |
| `+` | Decimal |
| `%` | Binary |
| `&` | Octal |
| `'` | PETSCII character |

## Commands

| Command | Action |
|---|---|
| `R` | Display registers (PC, SR, AC, XR, YR, ZR, BP, SP) |
| `;` | Modify registers (same format as R output) |
| `M [addr]` / `M [start] [end]` | Display memory (hex + PETSCII) |
| `> [addr] [bytes]` | Edit memory values |
| `D [addr]` | Disassemble |
| `A [addr] [mnemonic]` | Assemble instruction |
| `G [addr]` | Jump to address (or resume from breakpoint) |
| `J [addr]` | Call subroutine (JSR equivalent) |
| `F [start] [end+1] [val]` | Fill memory region |
| `C [start1] [end1] [start2]` | Compare memory regions |
| `H [start] [end] [bytes]` | Hunt for byte sequence |
| `T [start] [end] [dest]` | Transfer (copy) memory |
| `S "file" [start] [end]` | Save memory to disk |
| `L "file"` | Load from disk |
| `@` | Disk operations / drive status |

## BRK-Based Debugging

Insert `brk` instructions to halt at key points:
```assembly
next_col
    lda row_ct
    cmp #19
    bne +
    brk
+
```

## I/O and ROM Access

Prefix addresses with `8000` to access I/O registers and ROM:
```
M8000D000
>8000D020 07
```

## Freeze Monitor

Examines frozen program state (not live memory). Supports: `M`, `R`, `S`, `X`. Useful for comparing saved states.
