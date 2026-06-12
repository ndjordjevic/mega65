# lgblgblgb/fdc65bas

## Metadata
- Stars: 1
- Primary language: BASIC
- Default branch: main
- Latest release: none
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/lgblgblgb/fdc65bas

## Description
Fun experiment in BASIC65 for MEGA65 to read floppy disks with direct I/O

## README
A fun experiment in BASIC65 for the MEGA65: reading floppy disk sectors using direct I/O via POKE and PEEK to FDC (Floppy Disk Controller) registers, without using the DOS.

**Sub-projects:**

`read-demo/` — Simple sector read demonstration with hex dump. Uses fdc.prg (tokenized BASIC65 program) to read sectors and display them in hex. `fdc.d81` is a test disk image (not a general-purpose demo disk).

`imager/` — Attempt at a simple MS-DOS floppy imager in BASIC65.

**Why:** Mostly "why not" — a fun exercise demonstrating that BASIC65 can do low-level hardware I/O via POKE/PEEK. Documents the FDC register interface accessible from MEGA65 BASIC. The author notes they are "bad at [BASIC]" — intended as a learning/demonstration exercise.

## Top-level structure
- dir read-demo/ — sector read with hex dump (fdc.prg, fdc.d81)
- dir imager/ — MS-DOS floppy imager attempt
- dir build/ — build output
- file README.md, LICENSE, .gitignore
- file screenshot.jpg — screenshot of the demo running
