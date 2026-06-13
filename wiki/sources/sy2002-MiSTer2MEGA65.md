---
type: source
source_url: https://github.com/sy2002/MiSTer2MEGA65
tags: [mister2mega65, fpga-porting, vhdl, qnice, core-framework, mister, artix-7, vivado]
related: [MEGA65-mega65-core, 9Ib7z64z9N4-mister2mega65-explained]
product: mister2mega65
detail_level: standard
created: 2026-06-13
updated: 2026-06-13
---

MiSTer2MEGA65 (M2M) is a GitHub template repository and framework for porting MiSTer FPGA cores to the MEGA65. MiSTer runs its peripheral services (menus, ROM loading, disk mounting) on an ARM co-processor running Linux; the MEGA65 has no such co-processor. M2M bridges this gap by replacing MiSTer's ARM/Linux HPS layer with QNICE — a 16-bit System-on-a-Chip that runs on the Artix-7 FPGA itself, handling FAT32 SD access, on-screen menu overlay, and QNICE device bus communication. The framework is stable, GPL-3.0 licensed, and actively maintained (latest release V2.0.1, February 2025). The reference implementation is the [Commodore 64 for MEGA65](https://github.com/MJoergen/C64MEGA65); a community catalogue of M2M ports lives at https://sy2002.github.io/m65cores/. Directly relevant to understanding the [[MEGA65-mega65-core]] FPGA ecosystem and how third-party cores are built for it.

_All claims below are sourced from ../../raw/github/sy2002-MiSTer2MEGA65.md unless otherwise noted._

## What it does

M2M provides a reusable framework for anyone who wants to bring a MiSTer FPGA core (retro machine emulation — C64, arcade boards, home computers) to the MEGA65. You clone the template, fork the MiSTer core as a git submodule, wrap it in a thin VHDL glue layer, and the framework handles everything else: HDMI output (720p 50/60 Hz), LPCM audio, SD card access, virtual disk drives, on-screen help menu, board-level I/O. Supports all current board revisions: R3, R3A, R4, R5, R6.

## Key features

- **QNICE SoC** replaces MiSTer's ARM/Linux layer with on-FPGA firmware (Shell + callbacks); no external processor needed
- **Video pipeline**: HDMI 720p at 50/60 Hz, integer scaler, OSM overlay, configurable video filters
- **Virtual drives** (`vdrives.vhd`): SD card → disk-image interface, protocol-compatible with MiSTer's `sd/img`
- **Board HAL per revision**: separate constraint files and HAL VHDL for R3/R4/R5/R6; four Vivado projects share CORE sources, differ on board top + constraints
- **On-screen menu** (Help key): configurable pages, radio buttons, core settings — defined in `config.vhd`
- **HyperRAM support**: 8 MB available for core RAM that exceeds the 1.4 MB BRAM budget; requires CDC glue

## Architecture

The framework enforces a clean two-bucket split:
- **`CORE/`** — core-dependent, board-independent. Your porting work lives entirely here.
- **`M2M/`** — board-dependent, core-independent. The framework; you never edit these files.

The files you implement in `CORE/vhdl/`:

| File | Role |
|---|---|
| `main.vhd` | Glue — instantiates the retro machine RTL; wires raw RGB+CE video, signed 16-bit PCM audio, keyboard, joysticks, vdrives |
| `mega65.vhd` | Wrapper — instantiates `clk.vhd` + `main.vhd`; the M2M framework integrates at this boundary |
| `clk.vhd` | Xilinx MMCME2_ADV clock generation; replaces MiSTer's Quartus PLL; input is 100 MHz (not 50 MHz as on MiSTer) |
| `config.vhd` | On-screen menu definition: pages, groups, radio buttons; each item maps to a `C_MENU_*` constant index |
| `globals.vhd` | Core constants: clock speeds, BRAM sizes, QNICE device IDs, ROM/vdrive counts, audio coefficients |
| `keyboard.vhd` | Maps MEGA65 key-number scan codes to the machine's keyboard matrix or synthesizes PS/2 codes |

QNICE firmware is extended via `CORE/m2m-rom/m2m-rom.asm`: include framework files and implement callbacks (ROM validation, menu refresh, help text). The Shell handles 99% of firmware behaviour.

**Critical budget constraint:** The Artix-7 on the MEGA65 R6 has ~1.4 MB of usable BRAM after the M2M framework consumes ~200 KB. Fast machine RAM must fit within the remaining budget; anything above that goes to HyperRAM (~9-cycle latency), requiring Clock Domain Crossing glue between the main clock and HyperRAM controller.

## Installation

1. On GitHub, click "Use this template" on the M2M repo to create your project.
2. Fork the MiSTer core repo and add it as a git submodule.
3. Build the QNICE toolchain: `M2M/QNICE/tools/make-toolchain.sh`
4. Pre-build the firmware ROM: `CORE/m2m-rom/make_rom.sh`
5. Install Vivado 2022.2+ with Artix-7 support.
6. Open `CORE/CORE-R6.xpr` (or the target revision) in Vivado and synthesize.

## Example usage

The MiSTer → M2M service replacement pattern:

```
MiSTer status[63:0]  →  M2M osm_control (256-bit vector in config.vhd)
MiSTer ioctl_* ROM   →  QNICE device bus loader (device ID in globals.vhd)
MiSTer sd/img drive  →  vdrives.vhd (same protocol, just instantiate + configure)
MiSTer ps2_key       →  main_kb_key_num_i key-numbers (keyboard.vhd maps them)
MiSTer video_mixer   →  framework av_pipeline (feed raw RGB + clock-enable)
MiSTer ARM/Linux HPS →  QNICE SoC (provided by M2M; no action needed)
```

The Porting Guide documents all 12 phases in order, from Phase 0 (research dossier, CONF_STR analysis, BRAM budget) through Phase 12 (timing closure + hardware bring-up). Key traps: clock precision matters to PPM; `globals.vhd` constants must stay on single lines (make_rom.sh uses line-based awk); the firmware pre-build can fail silently on macOS.

## When to use

When you want to run an existing MiSTer FPGA core on the MEGA65 — whether for personal use or to contribute a community port. Also useful as a VHDL architecture study: the M2M framework shows how the MEGA65's Artix-7 FPGA, HyperRAM, HDMI pipeline, and QNICE SoC fit together in a real, working project. Less relevant if you're writing a new MEGA65 program from scratch (use [[MEGA65-mega65-core]] + standard BASIC/assembly workflow instead).

## Maintenance status

40 stars, 13 forks, GPL-3.0, VHDL primary. Latest release V2.0.1 (February 2025) fixed an R6 HyperRAM "jail bar" HDMI artefact and an R6-specific joystick port 2 bug. Version 2.0.0 (June 2024) added R6 support alongside R3/R3A/R4/R5, I2C, RTC, HyperRAM robustness improvements, and the Tyto2 HDMI framework. Active: last push 2026-06-11. The maintainer (sy2002) also maintains the QNICE FPGA CPU project (https://github.com/sy2002/QNICE-FPGA).

## Ecosystem

- **Reference implementation:** [C64MEGA65](https://github.com/MJoergen/C64MEGA65) — the definitive M2M port; used heavily in the Porting Guide for code examples
- **Community port catalogue:** https://sy2002.github.io/m65cores/
- **QNICE CPU:** https://github.com/sy2002/QNICE-FPGA — the on-FPGA 16-bit SoC that M2M uses for its firmware
- **MiSTer core catalogue:** https://mister-devel.github.io/MkDocs_MiSTer/ — where to find cores worth porting
- **Tutorial (files.mega65.org):** https://files.mega65.org?ar=898d573b-d30d-4438-8893-09455bd16400
- **Oliver Graf "MiSTer2MEGA65 Explained" video:** https://youtu.be/9Ib7z64z9N4 (the canonical intro video; first ~7 min explains FPGA/MEGA65 concepts before the porting details)
- Directly extends the [[MEGA65-mega65-core]] ecosystem; M2M ports compile as alternative bitstreams for the same Artix-7 FPGA
