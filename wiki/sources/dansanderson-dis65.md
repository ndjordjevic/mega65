---
type: source
source_url: https://github.com/dansanderson/dis65
tags: [disassembler, commodore-prg, 45gs02, 65ce02, acme-output, kickass-output, python-cli, reverse-engineering]
related: [dansanderson.com, wiebow.mega65.com, MEGA65-m65dbg]
product: dis65
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**dis65** is Dan Sanderson's small host-side disassembler for Commodore binaries — especially useful when you have a `.PRG` from a MEGA65 or C65 workflow and want readable assembly back out without opening a heavier reverse-engineering tool. It understands 6502, 65C02, 65CE02, and 45GS02 code, knows Commodore PRG load-address conventions, and can emit assembler-flavored output for ACME or Kick Assembler, making it a natural companion to [[dansanderson.com]]'s cross-development guidance, [[wiebow.mega65.com]]'s build pipeline, and the live-session debugging in [[MEGA65-m65dbg]].

_All claims below are sourced from ../../raw/github/dansanderson-dis65.md unless otherwise noted._

## What it does

`dis65.py` is a command-line disassembler for raw binaries and Commodore PRGs. By default it derives the starting address from a PRG header when present, otherwise starts at address 0, and it can also infer whether the front of a PRG is BASIC 2 or BASIC 65 from the conventional load addresses (`$0800` and `$2001`).

## Installation

There is no packaging or installer layer: clone or copy the repo and run the script with Python 3. The only in-tree automation is `make test`, which runs `python3 -m unittest dis65_test.py`.

## Key features

- CPU switch for `6502`, `65C02`, `65CE02`, or `45GS02` (default `45GS02`)
- PRG-aware input handling plus explicit `--prg` / `--no-prg`, `--address`, and `--offset` controls
- Output formatting toggle for `acme`, `kickass`, or plain output, plus `--annotated` to print addresses and raw data alongside the disassembly
- BASIC-aware front end for Commodore programs, not just pure machine-code blobs

## Architecture

The repo is intentionally small: almost all logic lives in the single `dis65.py` module, while `dis65_test.py` exercises instruction-table parsing, address parsing, BASIC-end detection, file disassembly, assembler-source rendering, and the 45GS02-specific redisassembly path. The `everyopcode.asm` / `.prg` / `.rpt` fixture trio provides a compact regression corpus for opcode coverage and PRG handling.

## Example usage

```text
python3 dis65.py file.prg
python3 dis65.py --assembler acme file.prg
python3 dis65.py --annotated --offset 60 file.dat
```

## Maintenance status

0 stars / 0 forks, MIT-licensed, default branch `main`, no releases, last pushed 2025-11-11. The README describes it as "a quickie for now, barely tested" and notes that Acme- and KickAss-specific spellings are still on the to-do list, so it is best treated as a practical utility rather than a polished packaged tool.
