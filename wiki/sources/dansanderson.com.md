---
type: source
source_url: https://dansanderson.com/mega65/
tags: [mega65-welcome-guide, cross-development, 45gs02-assembly, acme-assembler, basic-65, xemu, sd-card-setup, mega65-digest, vic-iv, rrb, petscii, sid, kernal, calypsi-c, llvm-mos]
related: [mega65.org, retrocogs.mega65.com, wiebow.mega65.com, dansanderson-easyasm65, dansanderson-joytest65, RetroCogs-Mega65Tutorials, dansanderson-dis65, dansanderson-tpn65, dansanderson-homebrew-mega65, dansanderson-mega65-pcfonts]
product: dansanderson
detail_level: deep
created: 2026-06-10
updated: 2026-06-12
---

Dan Sanderson's MEGA65 hub — the single best onboarding and programming tutorial resource in the ecosystem. Dan is a MEGA65 Steering Committee member and contributor to the official documentation, ROM, and FPGA core. The site hosts the **MEGA65 Welcome Guide** (19-chapter new-owner booklet), **Dan's MEGA65 Digest** (monthly newsletter with deep technical articles), and the **Cross Development series**. This wiki covers the Welcome Guide, the **complete Digest (all 44 posts)**, and 7 related **Lab Notes** articles (the deep technical posts under `/lab-notes/`, cross-tagged to MEGA65 but not part of the numbered Digest).

**How to use this page:** the tables below are an index — each row links to a raw page under `../../raw/web/dansanderson.com/`. Those raw pages are **condensed summaries** (key concepts, registers, and representative code), not full copies. For the complete article — every code listing and step — open the `- URL:` at the top of the raw page (the original on dansanderson.com). Answer chain: this index → raw summary → original URL.

_All claims below are sourced from ../../raw/web/dansanderson.com/ unless otherwise noted; each raw page links to its original URL for full detail._

---

## Site sections (not blog posts)

| File | URL | Summary |
|---|---|---|
| [hub.md](../../raw/web/dansanderson.com/hub.md) | /mega65/ | Landing page: Dan's role, project list, Digest overview |
| [welcome-guide.md](../../raw/web/dansanderson.com/welcome-guide.md) | /mega65/welcome/ | Full 12-chapter new-owner guide: SD cards, cores, ROM, Hypervisor, PAL/NTSC, microSD setup, core updates, file transfer, disk usage, version checking, community |

---

## Digest articles (all 44, newest first — matches the blog at /mega65/)

| Date | Article | Summary |
|---|---|---|
| 2026-05-25 | [calypsi-part-1.md](../../raw/web/dansanderson.com/calypsi-part-1.md) | Calypsi C toolchain: installation, hello world, PETSCII encoding, mega65.h register structs, multi-file projects, stdint types |
| 2026-04-22 | [pixies.md](../../raw/web/dansanderson.com/pixies.md) | Soft sprites via RRB: GOTOX for X positioning, Y offset (±7) and row masking for vertical positioning |
| 2026-03-14 | [raster-rewrite-buffer.md](../../raw/web/dansanderson.com/raster-rewrite-buffer.md) | RRB intro via Roguecraft DX: GOTOX, transparency, layering strategies, CHRCOUNT/LINESTEP, hot registers, DBLRR |
| 2025-11-29 | [every-pixel-a-color.md](../../raw/web/dansanderson.com/every-pixel-a-color.md) | Full Color Mode (FCM, 1 byte/pixel), Nibble Color Mode (NCM, 4-bit), Python image conversion, BASIC FCM loader |
| 2025-10-01 | [super-extended-attribute-mode.md](../../raw/web/dansanderson.com/super-extended-attribute-mode.md) | SEAM/CHR16: 8,192-char screen codes, full-palette multicolor, bitmap trick via unique screen codes |
| 2025-08-15 | [so-many-things.md](../../raw/web/dansanderson.com/so-many-things.md) | Commodore International revival, COMPUTE!'s Gazette return, VCF West recap, RetroCogs FCM/RRB tutorials |
| 2025-07-06 | [taste-the-rainbow.md](../../raw/web/dansanderson.com/taste-the-rainbow.md) | Custom palette entries, CHARDEF, 4 palette banks ($D070), Extended Background Color Mode (ECM), Low-res Multicolor Mode (MCM) |
| 2025-05-30 | [character-study.md](../../raw/web/dansanderson.com/character-study.md) | Character graphics fundamentals: screen/color memory layout, SCRNPTR register, resolution modes, T@&/C@& arrays |
| 2025-04-15 | [first-ten-years.md](../../raw/web/dansanderson.com/first-ten-years.md) | MEGA65 10-year history: C65 origins (1985), FPGA project (2010), 3 batches shipped (2022–2024), Easter egg hunt |
| 2025-03-25 | [whats-new-v0-97.md](../../raw/web/dansanderson.com/whats-new-v0-97.md) | v0.97 features: D64 mount, binary literals, 5-button joy, audio DMA IRQ, SAVEFL/GETIO KERNAL routines |
| 2025-02-19 | [screenful-compo-2025.md](../../raw/web/dansanderson.com/screenful-compo-2025.md) | Single-screen BASIC compo for the 10th anniversary; **Tall Character Mode (TCR)** 8×16 fonts; custom font loading |
| 2025-02-11 | [hosting-update-2025.md](../../raw/web/dansanderson.com/hosting-update-2025.md) | Admin: Digest moved Substack → Buttondown. No technical content |
| 2025-01-31 | [crossroads-part-2.md](../../raw/web/dansanderson.com/crossroads-part-2.md) | Ghidra setup for C64 (overlays, symbol files), IRQ handler at $11C4, sprite orientation transforms, data vs code distinction |
| 2024-12-12 | [santas-souped-up-mega65.md](../../raw/web/dansanderson.com/santas-souped-up-mega65.md) | SidPlay65, streaming video demos (HyperBallad/Duel), COPA65 clipboard, Sea Wolf disassembly by Gurce |
| 2024-11-15 | [crossroads-part-1.md](../../raw/web/dansanderson.com/crossroads-part-1.md) | Retro Debugger: character set at $2000, lives counter at $0011, half-step movement, memory filtering technique |
| 2024-10-21 | [up-up-down-down.md](../../raw/web/dansanderson.com/up-up-down-down.md) | Controller guide: 9-pin protocol, CIA assembly read, paddle registers ($D620-$D623), 3-button protocol, R3 vs R6 hardware |
| 2024-09-16 | [chicagoland.md](../../raw/web/dansanderson.com/chicagoland.md) | VCF Midwest recap; C65 prototype specs (3.54 MHz, 128K RAM); Filehost messaging; C64 core docs |
| 2024-08-26 | [introducing-easyasm.md](../../raw/web/dansanderson.com/introducing-easyasm.md) | EasyAsm on-device assembler: Acme-syntax subset, Edit mode workflow, memory layout, !to directive |
| 2024-07-17 | [lets-paint.md](../../raw/web/dansanderson.com/lets-paint.md) | BASIC 65 bitmap drawing (SCREEN/PEN/LINE/DOT/BOX/CIRCLE/ELLIPSE), generative art loops, graphing calculator, mouse/joy/keyboard paintbrush |
| 2024-06-17 | [kernal-of-truth.md](../../raw/web/dansanderson.com/kernal-of-truth.md) | KERNAL API: chrout ($FFD2), primm ($FF7D), plot ($FFF0), memory maps, vector routines must live at $1600–$1EFF; RTC clock project |
| 2024-05-31 | [racing-the-beam.md](../../raw/web/dansanderson.com/racing-the-beam.md) | Raster interrupts: IRQ/NMI, disabling KERNAL, custom handlers, raster IRQ setup ($D012/$D01A), ~2600 cycles/line |
| 2024-05-01 | [oh-right-april.md](../../raw/web/dansanderson.com/oh-right-april.md) | Brief update: Pascal65 compiler/IDE; llvm-mos SDK headers for C/C++ access to VIC-IV, SID, CIA, Hypervisor |
| 2024-03-14 | [justified-ancients.md](../../raw/web/dansanderson.com/justified-ancients.md) | PCM/DAC audio: Audio DMA system ($D720+), 8/16-bit samples, Audacity/ffmpeg conversion, 4-bit packing, MOD/Manche |
| 2024-02-25 | [release-day.md](../../raw/web/dansanderson.com/release-day.md) | v0.96 release: Ethernet transfer, core flashing menu (no JTAG for slot 0), 80×50 text mode, cartridge booting |
| 2024-02-15 | [sprite-attack.md](../../raw/web/dansanderson.com/sprite-attack.md) | VIC-II sprites: SPRITE/MOVSPR/SPRCOLOR/COLLISION, SpritEd in Freezer, SPRSAV animation, known bitmap-collision bug |
| 2024-01-15 | [new-hotness.md](../../raw/web/dansanderson.com/new-hotness.md) | v0.96 RC: Ethernet transfer, hardware-accelerated keyboard, mouse handling; batch ships June 2024 |
| 2023-12-14 | [robot-finds-kitten-3.md](../../raw/web/dansanderson.com/robot-finds-kitten-3.md) | Assembly game complete: getin ($FFE4), hardware RNG ($D7EF/$D7FE), CIA TOD timing, parallel arrays, Python data gen |
| 2023-11-29 | [mousepads-and-kofi.md](../../raw/web/dansanderson.com/mousepads-and-kofi.md) | Merch: 45GS02 Quick Reference mousepads/posters (all 6502/65CE02/45GS02 opcodes color-coded); Ko-fi launch |
| 2023-11-13 | [robot-finds-kitten-2.md](../../raw/web/dansanderson.com/robot-finds-kitten-2.md) | Assembly game: KERNAL routines, screen memory access, color memory (CRAM2K/$D030), 32-bit base page indirect |
| 2023-10-12 | [robot-finds-kitten-1.md](../../raw/web/dansanderson.com/robot-finds-kitten-1.md) | BASIC game architecture: T@&/C@& display, JOY(), RND(), DATA/READ/RESTORE, 4-phase program structure |
| 2023-09-16 | [mega65-survey-2023-results.md](../../raw/web/dansanderson.com/mega65-survey-2023-results.md) | Community Survey 2023 results (509 responses): demographics, hardware, software interests. Mostly community data |
| 2023-08-14 | [mega65-survey-2023.md](../../raw/web/dansanderson.com/mega65-survey-2023.md) | Survey invite; R4 skipped for R5; porting C64 BASIC to 80-col mode via screen-address tweaks + SPEED command |
| 2023-07-15 | [cross-development-2.md](../../raw/web/dansanderson.com/cross-development-2.md) | C via llvm-mos (`mos-mega65-clang`), Rust via rust-mos + mos-hardware; limitations (no float, ASCII not PETSCII) |
| 2023-06-20 | [cross-development-1.md](../../raw/web/dansanderson.com/cross-development-1.md) | Cross-dev workflow (Xemu, JTAG, PRG format), assembler comparison (Acme recommended), BASIC cross-dev (petcat, CBM PRG Studio, XC=BASIC) |
| 2023-05-14 | [bitmap-bonanza.md](../../raw/web/dansanderson.com/bitmap-bonanza.md) | VIC-III bitplane graphics, BASIC SCREEN/LINE/BOX/CIRCLE, SAVEIFF/LOADIFF, IFF bugs, NetPBM/ImageMagick workarounds |
| 2023-04-12 | [petscii-codes.md](../../raw/web/dansanderson.com/petscii-codes.md) | PETSCII history (PET→C64 redesign), control codes, 32-color palette, function keys, petcat curly-bracket syntax |
| 2023-03-14 | [rorschach-test-on-fire.md](../../raw/web/dansanderson.com/rorschach-test-on-fire.md) | 80×50 text mode (ESC+5), extended CHARDEF (512 codes), Monitor BRK fix; Mandelbrot in BASIC |
| 2023-02-14 | [what-i-wish-i-knew.md](../../raw/web/dansanderson.com/what-i-wish-i-knew.md) | Machine language intro: bits/bytes/hex, 45GS02 registers and instructions, monitor, Mega Assembler on-device |
| 2023-01-16 | [exploring-hardware.md](../../raw/web/dansanderson.com/exploring-hardware.md) | Hardware deep dive: Artix-7 FPGA, board revisions (R3→R6), peripherals, MEGAPhone project |
| 2022-12-23 | [back-to-basics.md](../../raw/web/dansanderson.com/back-to-basics.md) | BASIC 65 intro: DSAVE/MOUNT, petcat cross-dev, The Eleven editor, CBM PRG Studio, droiD64 |
| 2022-11-27 | [sounds-of-the-sid.md](../../raw/web/dansanderson.com/sounds-of-the-sid.md) | 4 SID chips (12 voices), SOUND/PLAY BASIC commands, PAL vs NTSC timing, ADSR envelopes |
| 2022-10-18 | [mega65-adventures.md](../../raw/web/dansanderson.com/mega65-adventures.md) | Interactive fiction: Z-machine via Ozmoo (Infocom games as D81), Inform 6/7, Dialog, PunyInform |
| 2022-09-17 | [the-next-batch.md](../../raw/web/dansanderson.com/the-next-batch.md) | Batch #2 announcement; CHARDEF custom character graphics in BASIC; Megazine type-in zine call |
| 2022-08-31 | [keeping-up-with-the-mega65.md](../../raw/web/dansanderson.com/keeping-up-with-the-mega65.md) | The inaugural Digest post: why the newsletter exists. No technical content |

---

## Lab Notes (cross-tagged to MEGA65, not part of the numbered Digest)

These live under `/lab-notes/` on Dan's site; several are among the most useful deep technical pieces in the whole catalog.

| Date | Article | Summary |
|---|---|---|
| 2022-12-04 | [advent-of-code-mega65.md](../../raw/web/dansanderson.com/advent-of-code-mega65.md) | Data transfer via D81, BASIC disk I/O (DOPEN/GET), pre-loading data at $40000 for assembly, ACME `!binary` embed |
| 2022-07-31 | [mega65-matrix-mode.md](../../raw/web/dansanderson.com/mega65-matrix-mode.md) | Matrix Mode debugger: Mega+Tab on-device or 2Mbaud serial; step/trace/breakpoint/watch without modifying code |
| 2022-07-26 | [mega65-monitor.md](../../raw/web/dansanderson.com/mega65-monitor.md) | MEGA65 monitor commands (M/D/A/G/J/F/H/T/S/L/@), number formats, BRK-based debugging, Freeze monitor |
| 2022-07-23 | [mega65-game-of-life-assembly.md](../../raw/web/dansanderson.com/mega65-game-of-life-assembly.md) | Game of Life in 45GS02 assembly (ACME); 300× faster; line buffers, zero-page indirect, BASIC starter structure at $2014 |
| 2022-07-20 | [mega65-game-of-life-basic.md](../../raw/web/dansanderson.com/mega65-game-of-life-basic.md) | Game of Life in BASIC 65; optimization study showing algorithmic wins over micro-opts; screen memory as board |
| 2022-06-17 | [adding-a-feature-to-mega65.md](../../raw/web/dansanderson.com/adding-a-feature-to-mega65.md) | ROM contribution walkthrough: ESC+Home feature; code size optimization; fixed C65 window-coordinate bug |
| 2022-06-12 | [welcome-mega65.md](../../raw/web/dansanderson.com/welcome-mega65.md) | First MEGA65 article: hardware overview, FPGA architecture, C64 mode, Xemu alternative |

Two other MEGA65-tagged Lab Notes were not captured (low value): `sega-adapter` (building a Sega controller adapter) and `mega65-basic-balloon` (a balloon sprite snippet). The `/projects/dans-mega65-digest/` page is an about-page for the Digest, also not captured. Fetch from the live site if needed.

## Ecosystem

Dense links into the rest of the ecosystem: [[mega65.org]] docs and Filehost, [[dansanderson-easyasm65]] (full manual in raw/github), [[RetroCogs-Mega65Tutorials]] (code curriculum), [[wiebow.mega65.com]] (complete build pipeline), Xemu, VICE/petcat, CBM PRG Studio, Kick Assembler, XC=BASIC.
