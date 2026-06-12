---
type: source
source_url: https://github.com/dansanderson/easyasm65
tags: [on-device-assembler, 45gs02, acme-syntax, screen-editor, edit-mode, basic-integration]
related: [dansanderson.com, MEGA65-mega65-code-snippets, dansanderson-tpn65, dansanderson-joytest65, dansanderson-bf-mega65]
product: easyasm
detail_level: standard
created: 2026-06-10
updated: 2026-06-12
---

EasyAsm by Dan Sanderson — an on-device 45GS02 assembler that turns the MEGA65 itself into a complete assembly development environment, using the machine's own screen editor and OS. The raw capture embeds the full README, which is the complete EasyAsm manual. The on-device counterpart to the cross-development workflows of [[dansanderson.com]] and [[wiebow.mega65.com]].

_All claims below are sourced from ../../raw/github/dansanderson-easyasm65.md unless otherwise noted._

## What it does

Supports all 45GS02 instruction types and addressing modes with a subset of Acme cross-assembler syntax — so source can move between EasyAsm and Acme. Edits source in the MEGA65 screen editor's Edit mode (line numbers, but treated as text); assembles to memory for testing or to disk for distribution; can generate a bootstrap loader; preserves source in memory across program runs and restores it even after abnormal exits.

## Installation

`MOUNT "EASYASM.D81" : BOOT` — installs to upper memory, clears program memory, binds the **Help** key to the interactive menu. Prompt changes from `READY.` to `OK.` in Edit mode (`EDIT ON`/`EDIT OFF`).

## Key features

Minimal memory footprint while editing or running; display settings preserved; `DSAVE` saves source (with Edit mode enabled); `MONITOR` available from the prompt. Example program shape: `10 !TO "SIMPLE", RUNNABLE` … `30 INC $D020` … `40 RTS`.

## Example usage

Type the source with line numbers in Edit mode, press Help → assemble and run. Save early and often — on-device development means a buggy program can take down the environment, though EasyAsm tries to preserve source.

## Maintenance status

v0.2 public beta (GPL-3.0; requires ROM beta 920401+ to assemble to disk; `!binary`/`!source` not yet implemented); syntax may change before 1.0. 15 stars, pushed 2025-04. Sponsorship via ko-fi.com/dddaaannn.

## Ecosystem

By the author of the Welcome Guide and Digest ([[dansanderson.com]]); fills the on-device niche alongside Eleven (BASIC IDE) and Mega Assembler listed in [[MEGA65-mega65-code-snippets]].
