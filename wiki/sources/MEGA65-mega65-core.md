---
type: source
source_url: https://github.com/MEGA65/mega65-core
tags: [fpga-core, vhdl, firmware, bitstream, builder]
related: [mega65.org, MEGA65-mega65-user-guide, mega65.atlassian.net]
product: mega65-core
detail_level: brief
created: 2026-06-10
updated: 2026-06-10
---

The MEGA65 FPGA core — the VHDL source of the machine itself ("Enhanced C65 running in FPGA"). Captured at brief detail: this wiki tracks it as the upstream of cores/bitstreams and release versions, not as a hardware-design study.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-core.md unless otherwise noted._

## What it does

Implements the complete MEGA65 hardware (45GS02 CPU, VIC-IV, etc.) in VHDL. Latest release: 0.97.2 (Sept 2025), matching the "0.97.2 R6A bugfix" release notes on [[mega65.atlassian.net]]. Default branch is `development`; 284 stars / 94 forks; pushed Feb 2026.

## Key features

Main documentation index at `docs/index.md` in-repo. BASIC 65 requires the licensed MEGA65 ROM from the Filehost; the free open-source OpenROM alternative is included. Automated builds at builder.mega65.org. It is also a git submodule of [[MEGA65-mega65-user-guide]], which documents its registers.

## When to use

Release tracking, flashing/core questions (which bitstream corresponds to which release), and as the authority of last resort on hardware behavior — read the VHDL when the books are ambiguous. Escalate to deep ingest if FPGA-level work begins.
