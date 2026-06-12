# lgblgblgb/megacyc

## Metadata
- Stars: 1
- Primary language: Assembly
- Default branch: main
- Latest release: none
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/lgblgblgb/megacyc

## Description
MEGA65 CPU cycles/opcode examiner and tester tool for MEGA65 and Xemu

## README
MEGAcyc is a cycle-timing tester for 45GS02 opcodes, designed to run on both real MEGA65 hardware and Xemu. Motivation: cycle counts at 40.5 MHz are not fully documented, and Xemu's CPU timing emulation has known inaccuracies. This tool provides a measurement framework to compare Xemu results against real hardware, helping validate and improve emulator accuracy.

**Method:** The tester runs a test for a full frame (to average out noise), then writes results to a D81 file mounted on the MEGA65 SD card. Results are extracted from the disk image and parsed by a Python script. The same test flow works on both Xemu and MEGA65, differing only in the transfer method.

**Toolchain required:** CC65 suite (cl65), xemu-xmega65, mega65_etherload, mega65_ftp, c1541, Python 3, GNU make, bash.

**Test targets:**
- `make xemutest` — test only Xemu; exit emulator after seeing directory listing
- `make megatest` — test on real MEGA65 (requires Ethernet remote control enabled via DIP switch + SHIFT+POUND)
- `make fulltest` — test both and compare
- `make parse` — parse already-collected results

**Results available in repo:** public/ directory has CSV/TSV files: Xemu vs MEGA65 comparison, MEGA65-only results, Xemu-only results, and comparison against Kibo's hand-measured reference results.

**Known issues:** SP-relative addressing mode shows anomalous cycle counts (40–50 instead of expected 7–8), suspected to be inter-opcode pipeline stalls from VHDL cache operations, not raw opcode timing. Other opcodes show 1-cycle discrepancies.

## Top-level structure
- file test.a65 — main 45GS02 assembly test program (CC65/CA65 format)
- file testbench.i65 — test framework includes
- file Makefile — build and test automation
- dir public/ — reference result files (TSV/CSV)
- dir result/ — output from test runs
- dir utils/ — Python parsing utilities
- file AUTHORS, LICENSE, README.md, .gitattributes, .gitignore
