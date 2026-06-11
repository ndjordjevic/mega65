# Back to BASICs

- URL: https://dansanderson.com/mega65/back-to-basics/
- Published: December 23, 2022
- Fetched: 2026-06-11

## Overview

Practical BASIC 65 development on and off the MEGA65: line-numbered programs, disk operations, advanced editing, and cross-development with petcat.

## BASIC 65 Basics

```
100 PRINT "ENTER A TEMPERATURE IN DEGREES FAHRENHEIT:"
110 INPUT F
120 C=(F-32)*5/9
130 PRINT F;" DEGREES FAHRENHEIT IS ";C;" DEGREES CELSIUS."
```

Line numbers by 10s standard practice (easy to insert intermediate lines).

## Disk Operations

```
DSAVE "filename"    : REM save to mounted D81
DSAVE "@filename"   : REM overwrite existing
MOUNT "work.d81"    : REM mount disk image
```

## Advanced Editing

- `LIST P` — paginated listing
- F9 / F11 — scroll through long programs line-by-line

## Cross-Development with petcat

petcat (included in VICE) converts plain-text BASIC to PRG:
```
petcat -w65 -o tempconv.prg -- tempconv.bas
```

PETSCII special chars in source: `{red}`, `{clr}`, `{CBM-@}`, etc.

## The Eleven Editor

Stephen Kleinert's Eleven editor: label-based (no line numbers), longer variable names, preprocessor directives. Compiles to standard BASIC 65 with no runtime overhead.

## PC-Side Tools

- **petcat**: VICE utility, cross-platform
- **CBM PRG Studio 4**: Windows IDE with MEGA65 support
- **DirMaster** (Windows) / **droiD64** (cross-platform): D81 image management
