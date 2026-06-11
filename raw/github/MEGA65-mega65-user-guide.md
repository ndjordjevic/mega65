# MEGA65/mega65-user-guide

## Metadata
- Stars: 82
- Primary language: TeX
- Default branch: master
- Latest release: release-2.0.0 — "Release 2.0.0: MEGA65 User's Guide, 2nd edition" (2024-02-29)
- License: none declared
- Homepage: (none)
- Forks: 54
- Pushed: 2026-04-08
- Fetched: 2026-06-10
- Final URL: https://github.com/MEGA65/mega65-user-guide
- Clone: full shallow clone at raw/github/MEGA65-mega65-user-guide/ (gitignored; ~392MB incl. assets/fonts; 87 root .tex files). Note: `mega65-core` and `mega65-libc` are git submodules, not initialized in the shallow clone.

## Description
MEGA65 User Guide — community effort to create a User Guide for the MEGA65 in the spirit of the original User Guide for the Commodore 64. This single repo is the LaTeX source of ALL official MEGA65 books.

## README
(key points, full text in clone at README.md)

- Latest typeset PDFs from the build pipeline: https://mega65.org/docs; official release increments on the GitHub releases page.
- Clone with `--recurse-submodules` (mega65-core, mega65-libc submodules).
- Toolchain: XeLaTeX (TeX Live / MacTeX / TeXworks), Inkscape ≥1.3.2 (`make generate-diagrams` converts SVG→EPS), GNU Make + GCC for supplemental C tools. Docker fallback: `make docker-image` then `make docker-mega65-book.pdf`.
- Build targets:

| Book | Build |
|---|---|
| User Guide | make mega65-userguide.pdf |
| Chipset Reference | make mega65-chipset-reference.pdf |
| Complete BASIC 65 Commands | make mega65-basic65-reference.pdf |
| Reference Guide | make referenceguide.pdf |
| Developer's Guide | make mega65-developer-guide.pdf |
| Guide to MEGA65 and FPGA Hardware | make hardwareguide.pdf |
| The Compendium | make mega65-book.pdf |
| Documentation Style Guide | make styleguide.pdf |

- `sandbox.tex` is the scratch file for drafting; VS Code + LaTeX Workshop recommended (build via Unix-style shell, not PowerShell).

## Docs
The books are assembled from chapter/appendix .tex files at repo root. The master documents (`mega65-book.tex`, `mega65-userguide.tex`, `mega65-developer-guide.tex`, `mega65-chipset-reference.tex`, `mega65-basic65-reference.tex`, `mega65-assembly-reference.tex`, `referenceguide.tex`) \include the chapter files.

Chapter files (selection): introduction.tex, settingup.tex, configuring.tex, beginninginbasic.tex, morebasic.tex, datainbasic.tex, basic-fragments.tex, sound.tex, sprites.tex, modes.tex, memory.tex, cpu.tex, cores-and-flashing.tex, updates.tex, using-disks.tex, transferring-files.tex, transferanddebugging.tex, emulators.tex, assemblers.tex, ccompilers.tex, libc.tex, developing-system-programs.tex, text-processing.tex, nexys4ddr-setup.tex, styleguide.tex, regulatory.tex.

Appendix files (the machine-readable spec — grep these): appendix-45gs02-registers.tex, appendix-instructionset.tex, appendix-viciv-registers.tex, appendix-sid-registers.tex, appendix-sound-registers.tex, appendix-45e100-registers.tex (Ethernet), appendix-45io27-registers.tex, appendix-4541-hw-iec.tex, appendix-cia6526-registers.tex, appendix-uart4551-registers.tex, appendix-rtc-registers.tex, appendix-special-registers.tex, appendix-memorymap.tex, appendix-dmagic.tex, appendix-hypervisor-calls.tex, appendix-kernal-jumptable.tex, appendix-basic65.tex (full BASIC 65 keyword reference), appendix-keywords.tex, appendix-basicabbreviations.tex, appendix-mathfunctions.tex, appendix-error-messages.tex, appendix-monitor.tex, appendix-keyboard.tex, appendix-screeneditorkeys.tex, appendix-petsciicodes.tex, appendix-screencodes.tex, appendix-screenmaps.tex, appendix-system-palette.tex, appendix-memorymap.tex, appendix-pinouts.tex, appendix-schematics.tex, appendix-troubleshooting.tex, appendix-accessories.tex, appendix-reference-tables.tex, appendix-decbinhex-tutorial.tex, appendix-target-specific.tex, appendix-mega65r2-flashing.tex.

Also: instruction_sets/ (directory of per-instruction data), examples/, elements/ + element-catalogue.tex, tools/, web-config/.

## Top-level structure
- *.tex (87 files) — all book chapters and appendices (see Docs above)
- Makefile, Dockerfile, .jenkinsfile — build system (XeLaTeX; Jenkins builds upload to Filehost)
- instruction_sets/ — instruction-set source data
- examples/ — example programs used in the books
- elements/, fonts/, frontcover/, assets/ — artwork, fonts, covers
- tools/ — build tooling; *.c helpers at root (keymap.c, screen-maps.c, prg2tex.c, document-memory.c, generate_condensed.c, libc-doc.c, test_basic_programmes.c)
- mega65-core, mega65-libc — submodule pointers (empty in shallow clone)
- references.bib, styleguide.tex — bibliography and authoring rules
