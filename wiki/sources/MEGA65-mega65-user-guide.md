---
type: source
source_url: https://github.com/MEGA65/mega65-user-guide
tags: [official-books-latex-source, basic-65-reference, 45gs02-registers, viciv-registers, memory-map, hypervisor-calls, xelatex, greppable-spec]
related: [mega65.org, dansanderson.com, MEGA65-mega65-core, RetroCogs-Mega65Tutorials]
product: mega65-user-guide
detail_level: deep
created: 2026-06-10
updated: 2026-06-10
---

The LaTeX source of **all five official MEGA65 books** (User's Guide, Developer's Guide, BASIC 65 Reference, Chipset Reference, and the ~1,433-page Compendium) in one community-maintained repo — 87 chapter/appendix `.tex` files, built with XeLaTeX via a Makefile and published to the Filehost by Jenkins. **This wiki keeps a full clone at `raw/github/MEGA65-mega65-user-guide/`**, which makes the entire official specification greppable plain text: this is the single most authoritative source in the wiki for any register, BASIC keyword, opcode, or memory-map question.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-user-guide.md unless otherwise noted._

## What it does

One repo, many books: master documents (`mega65-book.tex`, `mega65-userguide.tex`, `mega65-developer-guide.tex`, `mega65-chipset-reference.tex`, `mega65-basic65-reference.tex`, `referenceguide.tex`, `mega65-assembly-reference.tex`) include shared chapter files, so a fix lands in every affected book. Latest official release: 2.0.0, "User's Guide, 2nd edition" (2024-02); actively maintained (pushed 2026-04).

## Key features

Grep targets in the clone, by question type:
- **CPU/instructions**: `appendix-45gs02-registers.tex`, `appendix-instructionset.tex`, `instruction_sets/`, `cpu.tex`
- **Video**: `appendix-viciv-registers.tex`, `modes.tex`, `sprites.tex`, `appendix-screenmaps.tex`, `appendix-system-palette.tex`
- **Audio**: `appendix-sid-registers.tex`, `appendix-sound-registers.tex`, `sound.tex`
- **BASIC 65**: `appendix-basic65.tex` (full keyword reference), `appendix-keywords.tex`, `appendix-basicabbreviations.tex`, `appendix-error-messages.tex`, `beginninginbasic.tex`, `morebasic.tex`, `datainbasic.tex`
- **Memory/system**: `appendix-memorymap.tex`, `memory.tex`, `appendix-dmagic.tex`, `appendix-hypervisor-calls.tex`, `appendix-kernal-jumptable.tex`, `appendix-monitor.tex`
- **I/O chips**: `appendix-45e100-registers.tex` (Ethernet), `appendix-45io27-registers.tex`, `appendix-cia6526-registers.tex`, `appendix-uart4551-registers.tex`, `appendix-rtc-registers.tex`, `appendix-4541-hw-iec.tex`
- **User topics**: `settingup.tex`, `configuring.tex`, `cores-and-flashing.tex`, `using-disks.tex`, `transferring-files.tex`, `emulators.tex`, `appendix-keyboard.tex`, `appendix-petsciicodes.tex`, `appendix-troubleshooting.tex`
- **Dev tooling chapters**: `assemblers.tex`, `ccompilers.tex`, `libc.tex`, `transferanddebugging.tex`, `developing-system-programs.tex`

## Installation

`git clone --recurse-submodules` (mega65-core and mega65-libc are submodules — empty in this wiki's shallow clone); XeLaTeX + Inkscape ≥1.3.2 + Make/GCC, or the Docker fallback (`make docker-mega65-book.pdf`). Pre-built PDFs: mega65.org/docs.

## Example usage

`make mega65-book.pdf` builds the Compendium; each book has its own target. `sandbox.tex` is the drafting scratch file. For this wiki's purposes the more common usage is `grep -ri "<register or keyword>" raw/github/MEGA65-mega65-user-guide/*.tex`.

## Maintenance status

82 stars / 54 forks; no declared license; active (April 2026 push); built continuously by Jenkins (builder.mega65.org) with PDFs uploaded to the Filehost. Contributions follow the in-repo Documentation Style Guide (`styleguide.tex`).

## Ecosystem

The canonical upstream for everything described in [[mega65.org]]'s docs section; the PDFs it builds are the books referenced throughout [[dansanderson.com]] and [[retrocombs.com]]. Submodules tie it to mega65-core (FPGA) and mega65-libc (C library).
