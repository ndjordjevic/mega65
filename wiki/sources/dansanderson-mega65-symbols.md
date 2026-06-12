---
type: source
source_url: https://github.com/dansanderson/mega65-symbols
tags: [io-registers, symbols, acme, kick-assembler, ca65, cc65, ophis, rust, iomap, cross-development]
related: [dansanderson.com, dansanderson-easyasm65, MEGA65-mega65-core, MEGA65-mega65-tools, wiebow.mega65.com]
product: mega65-symbols
detail_level: standard
created: 2026-06-11
updated: 2026-06-11
---

Dan Sanderson's **mega65-symbols** — a generator (and a set of pre-generated files) that gives MEGA65 assembly/C/Rust programmers named symbols for every I/O register, so you write `mega65_io` names instead of looking up `$D0xx` addresses by hand. The symbols are derived from `iomap.txt`, which is built from the VHDL in [[MEGA65-mega65-core]], so they track the real hardware. The practical companion to any cross-development setup ([[wiebow.mega65.com]], [[dansanderson.com]] cross-development series).

_All claims below are sourced from ../../raw/github/dansanderson-mega65-symbols.md unless otherwise noted._

## What it does

Transforms `iomap.txt` (register map from the core's VHDL) into ready-to-include symbol files for six toolchains. Most users just take the pre-generated file for their assembler; the Python generator (`make-m65-symbols.py`) is only needed to regenerate against a newer iomap.

## Supported formats

ACME (`mega65_io.a`), Kick Assembler (`mega65_io.asm`), ca65 (`mega65_io.s`), cc65 (`mega65_io.h`), Ophis (`mega65_io.oph`), Rust (`mega65_io.rs`).

## Usage

Include the file for your toolchain, e.g. ACME: `!source "mega65_io.a"`. Then reference registers by name instead of raw addresses.

## When to use

Grab this at the **start of any MEGA65 assembly/C/Rust project** so register access is readable. Pin the file for the project's lifetime — the author warns symbol names may change in future updates. Pairs naturally with the [[wiebow.mega65.com]] Kick Assembler pipeline and Dan's own [[dansanderson-easyasm65]] on-device assembler.

## Ecosystem

By the author of the Welcome Guide and Digest ([[dansanderson.com]]); upstream data comes from [[MEGA65-mega65-core]] (VHDL → iomap.txt). Authoritative register documentation lives in the official Chipset Reference ([[MEGA65-mega65-user-guide]]); this turns that into usable symbols.
