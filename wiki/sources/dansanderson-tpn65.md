---
type: source
source_url: https://github.com/dansanderson/tpn65
tags: [basic-65, cross-development, eleven-like-syntax, petcat, python-cli, labels, preprocessor]
related: [dansanderson.com, dansanderson-easyasm65, MEGA65-eleven]
product: tpn65
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**TPN** is Dan Sanderson's host-side BASIC 65 transpiler: it lets you write source on a modern computer in an Eleven-like syntax, then emit plain BASIC text suitable for `petcat -w65` and MEGA65 PRG creation. Its value to this wiki is practical workflow coverage: it preserves the ergonomic ideas of Eleven — labels, long names, optional line numbers, and simple preprocessing — without requiring you to write the program on the MEGA65 itself, which makes it a direct companion to [[dansanderson.com]]'s cross-development material and the on-device contrast point [[dansanderson-easyasm65]] provides.

_All claims below are sourced from ../../raw/github/dansanderson-tpn65.md unless otherwise noted._

## What it does

TPN converts an Eleven-like source language into BASIC 65 text on a host PC. The intended pipeline is `python3 tpn.py mysource.bas | petcat -w65 -o myprogram.prg`, so the tool stops at readable BASIC output and leaves tokenization / PRG packaging to `petcat`.

## Installation

The dependency footprint is minimal: Python 3 is required, and nothing else in the repo needs to be installed. For actual MEGA65 output you also want `petcat`, either from the VICE emulator suite or the MEGA65 Filehost build linked in the README.

## Key features

- Eleven-style labels (`.label`, `goto label`) and low-profile line comments using `'`
- Long variable names with explicit `#declare`, including array shorthand and initializer shorthand
- `#define` / `#ifdef` preprocessing plus `#autodeclare` for looser workflows
- Optional manual line-number resets inside the source
- Multi-file input so a main program can be combined with reusable library files or build-specific header files
- ASCII-in / ASCII-out handling that preserves PETSCII-oriented string text for later `petcat` conversion

## Architecture

Almost all implementation logic lives in the single `tpn.py` file. It carries a reserved-word set for BASIC 65 keywords, parses directives such as `#declare`, `#define`, and `#ifdef`, assigns shortened two-character variable names, resolves labels to line numbers, and emits a contiguous BASIC listing. The repository's structure stays intentionally small: the examples (`example.bas`, `example2.bas`, `convertlib.bas`) demonstrate both single-file and library-style multi-file workflows, while `tpn_test.py` regression-tests parsing, directive handling, error paths, comment lowering to `REM`, and the CLI entrypoint.

## Example usage

```text
python3 tpn.py mysource.bas | petcat -w65 -o myprogram.prg
python3 tpn.py example2.bas convertlib.bas | petcat -w65 -o tempconvert.prg
make_tpn_source | python3 tpn.py | petcat -w65 -o myprogram.prg
```

## Maintenance status

The repo is MIT-licensed, has 0 stars / 1 fork, uses `main` as the default branch, has no tagged releases, and was last pushed on 2025-12-07. The README is explicit about scope: TPN is meant to be "roughly similar" to Eleven rather than a fully compatible clone, and future ideas still listed include an `#import` directive and a selectable target BASIC dialect.
