# Verification: the R6 MEGA65 has exactly ONE FPGA

> **Question settled:** does the current production MEGA65 (R6, shipped 2024) have one FPGA or more?
> **Answer: one** — a Xilinx Artix-7 200T. No MAX10, no Lattice CPLD, no other programmable logic.
> Verified against the official board schematic, not a web summary. — 2026-06-12

## Primary evidence — the actual R6 schematic

The official MEGA65 User's Guide embeds the Trenz **TE0765-06** mainboard schematic for the R6 board:

- Source file (in this repo, immutable): `raw/github/MEGA65-mega65-user-guide/assets/TE0765-06.PDF`
  (plus `TE0765-06-front.PDF`, `TE0765-06-back.PDF`)
- Referenced from: `raw/github/MEGA65-mega65-user-guide/appendix-schematics.tex` →
  `\section{MEGA65 R6 Schematics}`

Extracting every programmable-logic part number from those three PDFs:

```
$ pdftotext -layout TE0765-06.PDF - | grep -oiE 'XC7A[0-9]+T-[0-9A-Z]+' | sort -u
XC7A200T-2FBG484C        ← the one and only FPGA

$ grep -iE '10M0|MAX10|ALTERA|INTEL|LATTICE|MACHXO|LCMXO|CPLD|XC2C' (all 3 R6 PDFs)
(no matches)             ← no second programmable-logic device exists
```

**`XC7A200T-2FBG484C`** decodes as: Xilinx **Artix-7**, **200T** logic capacity, **FBG484** package,
**−2** speed grade, **C** (commercial) temp grade. It is the sole FPGA, and the only device on the board
that runs gateware — the entire `mega65-core` VHDL targets it.

## Corroborating evidence — User's Guide narrative

`raw/github/MEGA65-mega65-user-guide/appendix-target-specific.tex` explains the lineage that removed the
second FPGA:

- **R4** — *"The Intel™ MAX10™ helper FPGA has been **completely removed from the board**, simplifying the
  design… This also eliminates some difficult failure modes that could occur if the MAX10 FPGA were
  accidentally deconfigured."* (§ "Revision 4")
- **R5** — *"a relatively minor reworking of the R4 desktop PCB"* (power-regulator supply fixes, extra
  dip-switches via I2C, etc.). (§ "Revisions 5 and 6")
- **R6** — *"R6 is electrically identical to R5, and is the model that was included with MEGA65 production
  units shipped in the year 2024."* (§ "Revisions 5 and 6")

Chain: MAX10 gone at R4 → R5 minor rework of R4 → R6 electrically identical to R5 ⇒ **R6 has no MAX10.**
The keyboard is a separate PCB read over I2C IO-expanders (fixed-function silicon), so it adds no FPGA either.

## Why this note exists

Earlier in this learning project a web search reported "three FPGAs" and it was briefly written as fact.
That was true only for old boards (R2/R3 had the MAX10 helper). This note is the primary-source proof that
the **current** machine has one FPGA, so the claim never has to be re-litigated from memory or a web summary
again. See the accuracy-discipline rules in `../../AGENTS.md`.

## How to re-verify (≈30 seconds)

```bash
cd raw/github/MEGA65-mega65-user-guide/assets
pdftotext -layout TE0765-06.PDF - | grep -oiE 'XC7A[0-9]+T-[0-9A-Z]+' | sort -u
pdftotext -layout TE0765-06.PDF TE0765-06-front.PDF TE0765-06-back.PDF - \
  | grep -inE '10M0|MAX10|ALTERA|INTEL|LATTICE|MACHXO|LCMXO|CPLD|XC2C'   # expect: nothing
```
