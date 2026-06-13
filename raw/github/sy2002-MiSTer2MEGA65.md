# sy2002/MiSTer2MEGA65

## Metadata
- Stars: 40
- Primary language: VHDL
- Default branch: master
- Latest release: V2.0.1 (2025-02-22)
- License: GNU General Public License v3.0
- Homepage: (none)
- Fetched: 2026-06-13
- Final URL: https://github.com/sy2002/MiSTer2MEGA65

## Description

Framework to simplify porting MiSTer (and other) cores to the MEGA65.

## README

MiSTer2MEGA65
=============

MiSTer2MEGA65 is a framework to simplify porting MiSTer cores to the MEGA65.

Learn more by watching this YouTube video: https://youtu.be/9Ib7z64z9N4  
and get started by reading the MiSTer2MEGA65 Wiki: https://github.com/sy2002/MiSTer2MEGA65/wiki

**TL;DR**

1. Scroll up and press "Use this template" to start a new MiSTer2MEGA65 project. Fork the MiSTer core you want to port and make it a Git submodule.

2. Wrap the MiSTer core inside `CORE/vhdl/main.vhd` while adjusting the clocks in `CORE/vhdl/clk.vhd`. Provide RAMs, ROMs and other devices in `CORE/vhdl/mega65.vhd` and wire everything correctly.

3. Configure your core's behavior — start screen, ROM loading, Help menu — in `CORE/vhdl/config.vhd` and `CORE/vhdl/globals.vhd`.

**Status:** The M2M framework is stable and ready for use. The reference implementation is [Commodore 64 for MEGA65](https://github.com/MJoergen/C64MEGA65). A catalogue of community ports lives at https://sy2002.github.io/m65cores/

**Getting started:**
- Wiki "What is MiSTer2MEGA65": https://github.com/sy2002/MiSTer2MEGA65/wiki/1.-What-is-MiSTer2MEGA65
- Tutorial: https://files.mega65.org?ar=898d573b-d30d-4438-8893-09455bd16400
- MiSTer core catalogue: https://mister-devel.github.io/MkDocs_MiSTer/
- The Ultimate Porting Guide: https://github.com/sy2002/MiSTer2MEGA65/wiki/The-Ultimate-MiSTer2MEGA65-Porting-Guide

## Architecture

### Design principle

Files split into two orthogonal buckets:
- **CORE/** — core-dependent, board-independent (your port lives here)
- **M2M/** — board-dependent, core-independent (the framework; never touch)

Anything that depends on both must be decomposed into one of the two.

Top-level `.vhd` files exist per board revision: `top_mega65_r3.vhd`, `r4`, `r5`, `r6`.  
HAL files per revision: `hal_mega65_r3.vhd`, etc.

Supported boards: R3, R3A, R4, R5, R6.

### Key VHDL files (what you implement)

| File | Role |
|---|---|
| `CORE/vhdl/main.vhd` | Core glue — instantiates the retro machine RTL and wires video/audio/keyboard/joystick to M2M ports |
| `CORE/vhdl/mega65.vhd` | Core wrapper — instantiates clk.vhd + main.vhd; the M2M framework integrates here |
| `CORE/vhdl/clk.vhd` | Xilinx MMCM clock generation replacing MiSTer's Quartus PLL |
| `CORE/vhdl/config.vhd` | On-screen menu layout, pages, radio button groups |
| `CORE/vhdl/globals.vhd` | Constants: clock speeds, BRAM sizes, QNICE device IDs, ROM/vdrive counts |
| `CORE/vhdl/keyboard.vhd` | MEGA65 key-number → machine keyboard matrix or PS/2 code synthesis |

### M2M framework services (what you do NOT implement)

The M2M framework (M2M/ folder) provides:
- QNICE 16-bit SoC: FAT32 SD access, on-screen menu overlay (replaces MiSTer's ARM/Linux HPS)
- HDMI audio/video pipeline: 720p at 50/60 Hz, LPCM audio, integer scaler, OSM overlay
- Virtual drives (vdrives.vhd): SD card → disk image interface, protocol-compatible with MiSTer sd/img
- Board HAL: keyboard, joystick, HyperRAM, I2C, RTC, Ethernet (per revision)
- Constraint files: M2M/MEGA65-R3.xdc through R6.xdc (never edit)
- Firmware ROM (m2m-rom.asm): Shell provides 99%; you add assembly callbacks for core-specific behaviour

### QNICE processor

QNICE is a 16-bit CPU designed by sy2002. It runs the M2M firmware (Shell + callbacks) in a 64 KB address space, handles FAT32 SD reads, menu navigation, ROM loading, and QNICE device bus communication with main.vhd. Source: https://github.com/sy2002/QNICE-FPGA

### Memory budget

Critical constraint: the Artix-7 on the MEGA65 R6 has ~1.4 MB of usable BRAM after the framework consumes ~200 KB. Core RAM that fits goes in BRAM (fast, zero latency); above the budget it goes to HyperRAM (8 MB, ~9-cycle latency, requires CDC glue).

## MiSTer → M2M replacement map

| MiSTer service | M2M replacement | File to edit |
|---|---|---|
| `status[63:0]` bits | 256-bit `osm_control` vector | config.vhd + C_MENU_* constants |
| `ioctl_*` file download | CRT/ROM loader via QNICE device bus | globals.vhd device IDs + optional .asm |
| `sd/img` disk interface | vdrives.vhd (protocol-compatible) | globals.vhd constants |
| `ps2_key` PS/2 scan codes | `main_kb_key_num_i` key-number | keyboard.vhd matrix or PS/2 synthesis |
| Video pipeline | Framework av_pipeline (OSM, scaler, HDMI) | Feed raw RGB+CE to video_*_o ports |
| Audio IIR filter | Framework filter; configurable coefficients | globals.vhd audio constants |
| `RTC[64:0]` | `main_rtc_i` (pre-synchronized) | Wire through main.vhd if used |
| ARM/Linux HPS | QNICE SoC | — (provided by M2M) |

## Wiki content

The GitHub wiki (https://github.com/sy2002/MiSTer2MEGA65/wiki) is the primary documentation. Three sections:

**Section 1 — Getting Started**
1. What is MiSTer2MEGA65 — foundational overview; why M2M exists; the QNICE SoC design rationale
2. First Steps — setting up the template project, submodules, Vivado install
3. "Hello World" Tutorial — beginner hands-on

**Section 2 — Step-by-step Porting Guide**
4. Understand the MiSTer Core — anatomy of MiSTer rtl/ vs sys/; CONF_STR analysis
5. Project Set-up — cloning the template, QNICE toolchain build, firmware pre-build
6. Basic Wiring — wiring main.vhd ports
7. Get the Core to Synthesize — Vivado project setup; first synthesis
- XYZ. How to Release Your Core — publishing to the community

**Section 3 — Reference Guide**
- Architecture — CORE vs M2M split; HAL files per board revision
- Audio Filters — coefficients, filter types, configuration
- Caution and Loose Ends — known gaps, workarounds
- Individual VHDL file references (clk.vhd, config.vhd, globals.vhd, main.vhd, mega65.vhd)
- Clock Domain Crossing (CDC) — synchronization requirements and M2M helpers
- Debugging, Fatal Errors — black-screen decision tree, common Vivado errors
- File/Directory Browser, Help System, On-Screen Menu — user-facing features; configuration
- QNICE, m2m-rom.asm, Shell Memory Layout — firmware internals
- Video Filters, Video Pipeline and Output — scaler, HDMI timing, output modes
- Virtual Drives, RAMs and ROMs, Devices — storage; QNICE device bus
- HDMI Back Powering Problem — hardware gotcha; workaround documented

**The Ultimate MiSTer2MEGA65 Porting Guide** (wiki page) — 12-phase structured walkthrough from research through hardware bring-up:

Phase 0: Research (CONF_STR analysis, clock extraction, BRAM budget inventory, de-feature list)  
Phase 1: Template setup (clone, QNICE toolchain, Vivado 2022.2+)  
Phase 2–3: Core source prep + RTL conversion from Quartus/Verilog to Xilinx/VHDL  
Phase 4: Clock generation — replace Quartus PLL with Xilinx MMCME2_ADV; recalculate for 100 MHz input  
Phase 5: main.vhd glue — instantiate machine RTL, wire video (raw RGB+CE), audio (signed 16-bit PCM), keyboard, joysticks, vdrives  
Phase 6: Memory/device bus — dual-clock BRAMs + QNICE device IDs in globals.vhd  
Phase 7: HPS service replacement (see map above)  
Phase 8: config.vhd + globals.vhd — menu definition; C_MENU_* constants (order critical)  
Phase 9: m2m-rom.asm callbacks — ROM validation, menu refresh, help text  
Phase 10: Timing constraints (CORE.xdc) — generated clocks, CDC paths, multi-cycle exceptions  
Phase 11: Four Vivado projects (CORE-R3.xpr through CORE-R6.xpr) — share CORE sources, differ on board top + constraints  
Phase 12: Synthesis, timing closure, hardware bring-up; black-screen debug tree

**Key gotchas (TRAP callouts):**
- 1.4 MB BRAM budget — framework uses ~200 KB; fast machine RAM must fit in remainder
- Clock precision to PPM — wrong master clock detunes audio and breaks timing-sensitive software
- TRAP: Dynamic PLL reconfiguration (pll_cfg) has no Xilinx equivalent; pick one video standard for milestone 1
- TRAP: globals.vhd constants like C_VDNUM must stay on single lines — make_rom.sh uses line-based awk scraping
- TRAP: Firmware pre-build (make_rom.sh) can fail silently on macOS; always run on host before synthesis
- TRAP: Name collision — e.g. MiSTer rtl/ and M2M both define video_sync.vhd; wrong one silently breaks video
- What M2M does NOT offer: PS/2 mouse, dynamic output resolution, file save (ioctl upload), screen rotation, some copyrighted ROMs

## Top-level structure

```
CORE/                    ← core-dependent; your porting workspace
  CORE-R3.xpr            ← Vivado project for R3
  CORE-R4.xpr            ← Vivado project for R4
  CORE-R5.xpr            ← Vivado project for R5
  CORE-R6.xpr            ← Vivado project for R6
  CORE.xdc               ← core-specific timing constraints (you write these)
  m2m-rom/               ← firmware ROM build (QNICE assembly callbacks)
  vhdl/                  ← your VHDL: main.vhd, mega65.vhd, clk.vhd, config.vhd,
                            globals.vhd, keyboard.vhd

M2M/                     ← framework; never edit
  MEGA65-R3.xdc          ← board constraints R3
  MEGA65-R4.xdc          ← board constraints R4
  MEGA65-R5.xdc          ← board constraints R5
  MEGA65-R6.xdc          ← board constraints R6
  common.xdc             ← shared framework constraints
  vhdl/                  ← framework VHDL (HAL, QNICE SoC, video pipeline, vdrives)
  font/                  ← OSM font
  rom/                   ← QNICE firmware source (Shell, main.asm)
  tools/                 ← QNICE toolchain build scripts
  video_filters/         ← audio/video filter coefficient tables

doc/
  wiki/assets/           ← wiki images (mirrors doc assets; actual wiki is on GitHub)

AUTHORS                  ← contributors
VERSIONS.md              ← release history
```
