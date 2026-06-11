# MEGA65 Hardware System and Concepts

- URL: https://wiebow.mega65.com/2023/10/21/mega65-hardware-system-and-concepts/
- Published: 2023-10-21
- Fetched: 2026-06-11

## Overview

Explains the MEGA65's layered system architecture and how FPGA-based hardware sets it apart from traditional retro computers — a good conceptual orientation for newcomers.

## The five system layers

1. **FPGA Hardware** 2. **FPGA Cores** 3. **Hypervisor (HYPPO)** 4. **Operating System ROM** 5. **Software**

## FPGA Hardware

Three FPGA chips:
- **Main FPGA:** Xilinx Artix-7 (the primary one)
- **Secondary FPGA:** Altera MAX10 (electronic functions; forthcoming R5 boards omit this)
- **Keyboard FPGA:** Lattice (on the keyboard itself)

FPGAs ("field-programmable gate arrays") can be reconfigured to impersonate different ICs, allowing a minimal chip count on the motherboard.

## FPGA Cores

Core files are FPGA configurations; flash holds **8 slots**. Available cores include Commodore 64, ZX Spectrum, Game Boy, and arcade machines (Galaga, Xevious). Select a core at boot by holding **NO SCROLL**. Slot 0 is reserved for the factory core; 7 slots are user-available.

## Hypervisor (HYPPO)

An advanced task/system manager that provides services to programs. Activation triggers: system boot, machine configuration, system freeze, error handling, network/JTAG file reception, and specific key combinations.

## Freezer

Hypervisor-triggered, activated by the **RESTORE** key. Halts execution, freezes CPU state, loads the freezer system from SD card.
- **HELP key:** launches the MEGA Info tool (hardware versions, ROM, FPGA core, board revision)
- **ARROW keys:** select state slots; save/load machine states for debugging

Freezer changes are temporary; permanent changes require the hypervisor configuration utility (hold **ALT** at boot).

## Operating System ROM

File `MEGA65.ROM`, loaded from SD card by the hypervisor; provides the Kernel and BASIC. Multiple ROM files are supported, so you can test different operating systems without disrupting the primary install.

## Links

- Ultimate 64 (https://www.ultimate64.com/) — example of a C64 in FPGA
- Author's Mastodon: @wiebow (oldbytes.space); MEGA65 Discord
