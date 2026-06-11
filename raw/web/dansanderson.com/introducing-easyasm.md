# EasyAsm

- URL: https://dansanderson.com/mega65/introducing-easyasm/
- Published: August 26, 2024
- Fetched: 2026-06-11

## Overview

Introduction to EasyAsm — an on-device assembler for MEGA65 that requires no PC. Provides a powerful subset of Acme cross-assembler syntax within the BASIC 65 Edit mode environment.

## Key Features

- Works entirely on-device (no PC required)
- Uses BASIC 65 Edit mode (numbered lines, familiar environment)
- Acme-compatible syntax subset
- Two output modes:
  - **Assemble and Test**: run immediately in memory
  - **Assemble to Disk**: generate `.prg` files

## Memory Architecture

- Bank 0: $1E00–$1EFF (256 bytes) reserved
- Attic RAM: $8700000–$87FFFFF (1 MB) reserved
- Working space: $50000–$5FFFF (64 KB bank 5)
- Programs can use remaining memory freely

## Workflow

1. Mount `EASYASM.D81`
2. Boot into Edit mode (shows "OK" prompt)
3. Enter assembly source as numbered lines
4. `DSAVE "filename"` to save source
5. Help menu → assemble

The `!to` directive specifies output filename. `runnable` parameter auto-generates bootstrap code.

## Important Warning

"Save your work to disk, early and often." Programs that crash or enter infinite loops may overwrite source code in memory. Run/Stop + Restore halts execution and launches the Monitor.

## Future Development

Planned: binary file embedding, multi-file source, annotated listings, symbol inspection, macros, modern IDE-style editor.

## See Also

Full EasyAsm manual in `raw/github/dansanderson-easyasm65.md`.
