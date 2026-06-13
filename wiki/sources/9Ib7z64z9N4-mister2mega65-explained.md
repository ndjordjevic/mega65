---
type: source
source_url: https://www.youtube.com/watch?v=9Ib7z64z9N4
tags: [mister2mega65, fpga, alternate-cores, c64-core, qnice, video-tutorial, oliver-graf, porting]
related: [sy2002-MiSTer2MEGA65, MEGA65-mega65-core, lgblgblgb-xemu]
product: mister2mega65-explained
detail_level: standard
created: 2026-06-13
updated: 2026-06-13
---

An 18-minute explainer video by Oliver Graf (March 2022) covering the MiSTer2MEGA65 (M2M) framework from the ground up — what it is, why direct MiSTer core loading is impossible, and how M2M bridges the gap. The first ~7 minutes are the clearest accessible spoken introduction to FPGA basics, MEGA65 hardware, MiSTer hardware, and why the two aren't directly compatible; the remainder demonstrates an early-alpha C64 core running the Comaland demo and Doc Cosmos, with a first look at the M2M on-screen menu. Essential context video for anyone approaching [[sy2002-MiSTer2MEGA65]] for the first time.

_All claims below are sourced from ../../raw/youtube/9Ib7z64z9N4-mister2mega65-explained.md unless otherwise noted._

## What the video is about

Oliver Graf explains why MEGA65 users can't simply run MiSTer FPGA cores on their hardware, and introduces the MiSTer2MEGA65 framework as the solution. The video covers: FPGA fundamentals (why FPGA is not emulation); MEGA65 hardware specs (Xilinx Artix-7, 215k LEs, no HPS); MiSTer hardware (Cyclone 5 SoC with ARM Cortex-A9 HPS running Linux); the key difference (MEGA65 has no ARM/Linux layer, different I/O ports); M2M's approach (QNICE soft-CPU replaces the ARM HPS, VHDL abstraction layer for keyboard/HDMI/audio/SD); and a live demo of an early C64 core port.

## Key points by chapter

**Intro (0:00):** The video was prompted by the MiSTer2MEGA65 framework, not the originally promised Mandelbrot/full-color-mode video.

**What are we talking about? (0:30):** The MEGA65 is an FPGA machine running an enhanced C65 core. It is not fully C64-compatible. MiSTer has many vintage platform cores. The question is: can we run those cores on the MEGA65? (Answer deferred — requires FPGA basics first.)

**FPGA Basics (1:47):** An FPGA is a reconfigurable chip — logical elements, flip-flops, and memory cells reconnected by a bitstream. It is not an emulator: circuits behave at the hardware level, including timing and electrical levels. This is also why you cannot run an FPGA core inside Xemu — full circuit simulation at real-time speed is too computationally expensive even for 1 MHz CPUs.

**MEGA65 Basics (2:51):** Complete home computer — one case, keyboard, 3.5" floppy. Custom PCB with Xilinx Artix-7 (215,000 LEs, ~13 Mbit BRAM). No HPS (Hard Processing System — a fixed CPU you can't change). Interfaces: VGA, HDMI, IEC, dual SD, DB9, PETSCII keyboard, cartridge slot.

**MiSTer Basics (4:07):** Not a complete system — runs on Terasic DE10-Nano with Intel Cyclone 5 SoC. The Cyclone 5 has both an FPGA (110,000 LEs, 5.5 Mbit BRAM) and a dual-core ARM Cortex-A9 running Linux. The ARM (HPS) handles SD card access, USB, menus, and I/O — functionality the FPGA core itself doesn't provide.

**Differences (5:36):** Direct core loading is impossible because: (1) the MiSTer relies on the ARM/Linux HPS for SD card, USB, and peripheral I/O that the MEGA65 has no equivalent of; (2) the MEGA65 has its own keyboard interface and I/O ports incompatible with MiSTer's expansion boards. However, the MEGA65's Artix-7 is larger than the Cyclone 5 FPGA — so resource headroom is not the problem.

**MiSTer2MEGA65 (6:24):** M2M is a VHDL framework (not a core player) that provides hardware abstraction for the MEGA65: keyboard, HDMI, audio, RAM interface, and QNICE — a 16-bit soft-CPU that runs on the Artix-7 and replaces the ARM HPS. QNICE handles the on-screen display and SD card access (analogous to the MEGA65's Hypervisor and Freezer). The key design principle: a porter should only need to change how the MiSTer core connects to the M2M framework, not modify the core itself — making future MiSTer core updates easier to integrate.

**Schematics (7:28):** Visual comparison of the two architectures. MiSTer: Cyclone 5 SoC with FPGA + ARM. MEGA65: Artix-7 FPGA with M2M framework (in light orange) and the ported core. M2M lives inside the bitstream alongside the core. Changes to MiSTer cores could also flow back upstream.

**How to port a core (8:48):** Porting requires hardware description language (VHDL/Verilog) skills — it is design work, not just programming. As of March 2022, two cores were ported and a third (C64) was nearly at alpha. Documentation was described as "bare-bones" but growing. Community (MEGA65 Discord) is the main support channel.

**C64 core demo (10:08–18:26):** Live demo of the early-alpha C64 core — bitstream loaded via `m65` tool; Comaland demo by Oxyron runs successfully; first look at the M2M on-screen menu (Help key), which at the time had Hz selection and triple-buffering but not yet disk or cartridge switching; Doc Cosmos by Shallan50k runs as a joystick game demo.

**Outro (18:26):** Framework created by MJoergen and Sy2002. Community questions: MEGA65 Discord.

## Notable quotes

> "The FPGA is not an emulation because it really reassembles the circuits and hardware. There is no modern processor inside that will try to act like a vintage processor — the circuits and elements on the FPGA will behave like a real circuit down to timing and electrical levels."

> "It is not a MiSTer core player which you simply run on your MEGA65 to play MiSTer cores — this is not possible. It is a base that provides a hardware abstraction for the MEGA65 system by providing VHDL components that allow for easy interfacing."

> "The idea of the framework is that you should not need to change the MiSTer core — you only need to change the way the core is connected to the framework."

## Speaker context

Oliver Graf is a MEGA65 community member and content creator who produces tutorial and explainer videos about the MEGA65. This video is from March 2022, when M2M had two ports complete and the C64 core was approaching alpha. He is distinct from the M2M framework authors (Sy2002 and MJoergen).
