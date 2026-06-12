# dansanderson/dis65

## Metadata
- Stars: 0
- Primary language: Python
- Default branch: main
- Latest release: none
- License: MIT License
- Forks: 0
- Pushed: 2025-11-11
- Homepage: (none)
- Fetched: 2026-06-12
- Final URL: https://github.com/dansanderson/dis65

## Description
A simple disassembler for 6502, 65C02, 65CE02, and 45GS02 CPUs, and Commodore PRGs

## README
# dis65

A simple disassembler for 6502, 65C02, 65CE02, and 45GS02 CPUs, and Commodore PRGs.

Usage: `python3 dis65.py [options] <filename>`

Options:

| Option | Description |
|-|-|
| `--address <addr>` | Starting address of the file, in decimal (no prefix) or hexadecimal (with `$` or `0x` prefix). Default is to derive from the file if it is a PRG, or 0 otherwise. |
| `--prg` | File is a PRG file with a two byte starting address header. If `--address` is specified, the two byte header is consumed, but ignored. Default is yes if filename ends in ".prg", no otherwise. |
| `--no-prg` | File is a binary file (without a two-byte address header). |
| `--offset <offset>` | Offset from start of file from which to start disassembly. Default is 0. |
| `--cpu <cpu>` | The CPU to assume. Either `6502`, `65C02`, `65CE02`, or `45GS02`. Default is `45GS02`. |
| `--basic <version>` | Assume the PRG starts with BASIC code. Supported versions are `2` and `65`. Default is derived from the starting address: $0800 is BASIC 2, $2001 is BASIC 65. |
| `--assembler <name>` | The output assembler syntax: `acme`, `kickass`, or `none`. Default is `none`. |
| `--annotated` | Output source with addresses and data on the same line, in hexadecimal. |

Examples:

```
python3 dis65.py file.prg

python3 dis65.py --prg file.dat

python3 dis65.py --address $1600 file.dat

python3 dis65.py --assembler acme file.prg

python3 dis65.py --annotated --offset 60 file.dat
```

Still to-do: Acme and Kickass-specific spellings.

This is a quickie for now, barely tested. If you find this useful, please help [report bugs and feature requests](https://github.com/dansanderson/dis65/issues)!

## Top-level structure
- `dis65.py` (27.1 KB) — single Python module and CLI entrypoint; tests import `Disassembly`, `ByteBlock`, `Instruction`, `find_end_of_basic`, `get_instructions`, `make_instruction_from_text`, `parse_addr`, `disassemble`, `make_assembler_source`, `disassemble_file`, and `redisassemble_45gs02` from here.
- `dis65_test.py` (15.4 KB) — unittest suite covering opcode-table parsing, address parsing, CPU selection (`6502` / `65C02` / `65CE02` / `45GS02`), data-model helpers, and failure cases.
- `everyopcode.asm` (4.2 KB) — assembly fixture used for opcode-coverage testing.
- `everyopcode.prg` (994 B) — Commodore PRG fixture for PRG-aware disassembly cases.
- `everyopcode.rpt` (17.9 KB) — expected report/output fixture for regression comparison.
- `Makefile` (41 B) — minimal test target: `make test` runs `python3 -m unittest dis65_test.py`.
- `LICENSE`, `.gitignore` — licensing and repo housekeeping.
