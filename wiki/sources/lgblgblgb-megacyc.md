---
type: source
source_url: https://github.com/lgblgblgb/megacyc
tags: [cycle-timing, opcode-testing, 45gs02, xemu-validation, cross-development, cc65, mega65-hardware-testing]
related: [lgblgblgb-xemu, lgblgblgb-mega65-utils]
product: megacyc
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**megacyc** is LGB's cycle-timing tester for 45GS02 opcodes, designed to run identically on both real MEGA65 hardware and [[lgblgblgb-xemu]]. Its primary purpose is to measure the actual clock cycle cost of each opcode at 40.5 MHz — data that is not fully documented — and to expose timing discrepancies in Xemu's CPU emulation by comparing hardware and emulator results.

_All claims below are sourced from ../../raw/github/lgblgblgb-megacyc.md unless otherwise noted._

## What it does

Runs a timing test for a full video frame per opcode (to average noise), writes results to a D81 file on the SD card, extracts and parses the results with a Python script. The same flow runs on Xemu (disk written to virtual image) and on real MEGA65 (disk transferred via Ethernet/mega65_ftp). Comparison tables show discrepancies between Xemu and hardware, and also against Kibo's manually measured reference values.

## Installation

Requires: CC65 suite (`cl65`), xemu-xmega65, mega65_etherload, mega65_ftp, c1541, Python 3, GNU make, UNIX-like OS. Paths configurable in Makefile.

**For Xemu only:** `make xemutest` — exit emulator after directory listing appears.

**For real MEGA65:** `make megatest` — requires Ethernet remote control enabled (DIP switch + SHIFT+POUND), `OPCYCLES.D81` present on SD card.

**Full comparison:** `make fulltest` or `make xemutest && make megatest && make parse`.

## Key features

- Tests all 45GS02 opcodes, one frame per test
- Produces CSV/TSV comparison tables: Xemu vs MEGA65, MEGA65-only, Xemu-only, vs Kibo's reference
- Reference comparison detects regressions against hand-measured ground truth
- Results committed in `public/` for offline consultation

## Architecture

`test.a65` — main 45GS02 test program (CA65/CC65 format); `testbench.i65` — test framework includes; `Makefile` — orchestrates build, run, extract, compare; `utils/` — Python result-parsing scripts; `public/` — pre-committed TSV/CSV results.

## Example usage

```sh
make xemutest   # test Xemu; exit after directory listing
make fulltest   # test both Xemu and real MEGA65, then compare
```

## Maintenance status

1 star, 0 forks, GPL-3.0, last pushed 2025-04-10. Working but noted as "quick try" quality. Known anomalies: SP-relative addressing shows 40–50 cycles instead of expected 7–8, suspected due to VHDL pipeline stalls rather than raw opcode cost.

## Ecosystem

Complements [[lgblgblgb-xemu]] by providing ground truth against which Xemu's CPU timing can be validated. Also relies on CC65 and mega65_ftp from the broader MEGA65 toolchain.
