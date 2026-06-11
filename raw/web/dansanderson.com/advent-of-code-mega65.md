# Advent of Code on the MEGA65

- URL: https://dansanderson.com/lab-notes/advent-of-code-mega65/
- Published: December 4, 2022
- Fetched: 2026-06-11

## Overview

Practical guide for doing Advent of Code puzzles on the MEGA65: data transfer, BASIC disk I/O, Mega Assembler, and ACME cross-assembly with embedded data.

## Data Transfer to MEGA65

Use microSD card + D81 disk images (FAT32). Tools:
- **DirMaster** (Windows desktop)
- **droiD64** (Java, cross-platform)
- **cbmconvert / c1541** (command-line)

## Reading Data in BASIC 65

```basic
5 V$=""
10 DOPEN#1,"AOC01"
20 GET#1,B$
30 IF ST THEN 110
40 IF ASC(B$)=10 THEN 70   : REM newline = end of line
50 V$=V$+B$
60 GOTO 20
70 V=VAL(V$)               : REM convert string to number
80 PRINT V
90 V$="" : GOTO 20
110 DCLOSE#1
```

## Pre-loading Data for Assembly

BASIC loader puts input data into upper memory ($40000), then Mega Assembler runs:

```basic
10 AD=$40000
20 DOPEN#1,"AOC01"
30 GET#1,B$ : IF ST THEN 80
40 POKE AD,ASC(B$) : AD=AD+1
50 GOTO 30
80 DCLOSE#1
90 POKE AD,10 : POKE AD+1,10 : POKE AD+2,0  : REM terminators
```

## Upper Memory Access in Assembly

45GS02 base page indirect for accessing memory beyond 64 KB:
```assembly
; set base page $1600 with 32-bit pointer to $40000
lda [$fc],z   ; read from upper bank
```

## Cross-Assembly: Embed Data with ACME

```asm
!cpu m65
!to "aoc01-asm.prg", cbm
* = $2001
; BASIC one-liner header
!8 $12,$20,$0a,$00,$fe,$02,$20,$30,$3a,$9e,$20
!pet "$2014"
!8 $00,$00,$00

data:
!binary "input.txt"
!byte 10,10,0
```

Gives nearly 54 KB of code space; deploy via `m65` serial tool for rapid iteration. **Recommended approach** for complex AoC puzzles.
