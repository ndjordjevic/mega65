# RetroCogs/Mega65Tutorials

## Metadata
- Stars: 12
- Primary language: Assembly
- Default branch: main
- Latest release: none
- License: none declared
- Homepage: (none)
- Forks: 2
- Pushed: 2025-12-24
- Fetched: 2026-06-10
- Final URL: https://github.com/RetroCogs/Mega65Tutorials

## Description
Various tutorials for coding in 45gs02 on the Mega65.

## README
README is minimal (~144 bytes; emulator invocation fragments referencing Xemu flags like `-initvideostd`, `-autoload`, `-prg bin/<name>.prg -uartmon :4510`). The repo is documented by its companion blog, retrocogs.mega65.com, and by the tutorial source files themselves.

## Docs
No docs/ directory. The numbered tutorial sources are the curriculum (each pairs with a blog post on retrocogs.mega65.com):

- tutorial_0_blank.asm, tutorial_0_hdmicolor.asm — minimal program skeletons
- tutorial_1_screens.asm — VIC-IV screen layout (CHRCOUNT/DISPROWS/LINESTEP, H640/V400)
- tutorial_1b_textenter.asm — text entry
- tutorial_2_scrolling.asm — hardware scrolling
- tutorial_3_fcm.asm, tutorial_3a_fcm_rrb.asm — Full Color Mode (+RRB)
- tutorial_4_ncm.asm — Nibble Color Mode
- tutorial_5_rrbScroll.asm — RRB scrolling
- tutorial_6_rrbParallax.asm — RRB parallax layers
- tutorial_7_rrbObjs.asm — RRB objects
- tutorial_8_advPixies.asm, tutorial_9_superAdvPixies.asm, tutorial_10_flipPixies.asm — software-sprite (pixie) engines of increasing sophistication

Shared includes: mega65macros.asm, mega65system.asm (system setup/macro library used by all tutorials).
Assets: fcm_test / ncm_test / ncm_sprite PNG sources with matching _chr.bin and _pal.bin converted character/palette data; example screenshots (rrbScroll_example.png, rrbSpr_example.png, rrbTutorial_example.png).
Build: makefile + build/ directory; Kick Assembler syntax; Xemu launch flags embedded in README/makefile (`-uartmon :4510` for monitor debugging).

## Top-level structure
- tutorial_*.asm (15) — numbered tutorial programs
- mega65macros.asm, mega65system.asm — shared library
- makefile, build/ — build pipeline
- *.png + *_chr.bin + *_pal.bin — graphics assets and converted data
- .gitattributes, .gitignore
