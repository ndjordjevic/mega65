# dansanderson/mega65-symbols

## Fetch log
- Inbox URL: https://github.com/dansanderson/mega65-symbols
- Final URL: https://github.com/dansanderson/mega65-symbols
- Fetched: 2026-06-11
- Mode: standard (brief GitHub capture — README + repo metadata)

## What it is

"A generator for producing symbols files for MEGA65 I/O for various assemblers, based on the `iomap.txt` built from the VHDL in mega65-core."

The problem it solves: MEGA65 assembly programmers constantly reference I/O register addresses ($D0xx etc.). Rather than hand-looking-up hex values from the Chipset Reference, you include a pre-generated symbol file so you can write register **names** instead of raw addresses.

## How it works

- Source of truth: `iomap.txt`, itself generated from the VHDL in [[MEGA65-mega65-core]] — so the symbol names track the actual hardware definitions.
- Core tool: `make-m65-symbols.py` (Python) transforms `iomap.txt` into per-assembler symbol files.
- The repo ships **pre-generated** symbol files, so most users never need to run the generator — just grab the file for their toolchain.

## Supported output formats (6)

| Assembler / compiler | Generated file |
|---|---|
| ACME assembler | `mega65_io.a` |
| Kick Assembler | `mega65_io.asm` |
| ca65 assembler | `mega65_io.s` |
| cc65 C compiler | `mega65_io.h` |
| Ophis assembler | `mega65_io.oph` |
| Rust compiler | `mega65_io.rs` |

## Usage

Include the generated file in your project, e.g. for ACME:

```
!source "mega65_io.a"
```

## Maintenance note

The author warns that future updates may change symbol names, and recommends generating/copying the symbol file at project start and keeping it stable for the project's lifetime rather than constantly re-syncing. ~12 commits; languages reported as Assembly 63.2% / C 34.7% / Python 2.1% (the C/asm being the example/test material).

## Links
- Repo: https://github.com/dansanderson/mega65-symbols
- Upstream data: iomap.txt derived from github.com/mega65/mega65-core VHDL
