---
type: overview
domain: "MEGA65 retro computer"
created: 2026-06-10
updated: 2026-06-12
sources: []
---

# MEGA65 retro computer — overview

The official site [[mega65.org]] establishes the foundation of this domain: the MEGA65 is an open-source FPGA realization of the unreleased Commodore 65 — a real 8-bit computer roughly 40x faster than a C64, highly compatible with both C64 and C65, shipping with the MEGA-OS hypervisor, BASIC 65, 4 SIDs, dual SD slots, and Ethernet. The site maps the entire official ecosystem: four free PDF manuals (User's Guide, BASIC 65 Reference, Developer's Guide, and the 1,433-page Complete Compendium), the Confluence documentation wiki, the Filehost software repository, the Xemu emulator onboarding path (including ROM patching and the 263-title ALL_INTROS package), the alternative-cores catalog that reflashes the FPGA into other machines, and the community channels (Discord, Forum64, Reddit, YouTube).

[[dansanderson.com]] is the ecosystem's premier onboarding and tutorial hub, run by Steering Committee member Dan Sanderson. Its Welcome Guide supplies the new-owner mental model — SD card conventions, FPGA cores in 7 slots, the `MEGA65.ROM` file, the Hypervisor, PAL/NTSC — while the Cross Development series and monthly Digest cover the developer workflow: write on a modern host, cross-assemble with Acme (native 45GS02 support) or Kick Assembler (via fork), convert BASIC with `petcat -w65` or compile XC=BASIC, then run in Xemu (`-prg`) or push to hardware via JTAG/M65Connect. It also documents the PRG file format and the trick of prepending a BASIC `SYS` launcher to machine-code programs.

[[retrocombs.com]] adds the getting-started / how-to layer: Steven Combs' 32 hands-on blog posts cover setup, configuration, running Xemu on every OS (Mac/ChromeOS/uConsole), building a MEGA65 on a Nexys FPGA board, patching the original C65 ROM, BASIC 65 conversions, and accessories — anchored by his chapter-by-chapter video-and-blog companion to the official User's Guide. He also maintains a curated resource page of download links (latest `MEGA65.ROM`, SD Card Essentials, GEOS 65 beta, the full-featured C64 core) and tools (Xemu, M65 Connect, `m65`/`mega65_ftp`). The consumer-friendly, operational complement to the more programming-focused [[dansanderson.com]].

[[retrocogs.mega65.com]] supplies the register-level graphics knowledge: VIC-IV screen layout via CHRCOUNT/DISPROWS/LINESTEP, H640/H320 and V400/V200 scaling semantics ($D031), hardware scrolling, FCM/NCM color modes, and the Raster Rewrite Buffer — a 2048-pixel line buffer with GOTOX characters that enables layered backgrounds and software sprites ("pixies") under Super Extended Attribute Mode. Each tutorial maps to working Kick Assembler code in the companion Mega65Tutorials repo.

[[wiebow.mega65.com]] contributes the most concrete build pipeline: Kick Assembler's 65CE02/45GS02 fork (`.cpu _45gs02`), `c1541` for D81 images, Xemu for fast iteration, and Ethernet deployment to real hardware via `mega65_ftp -e` and `etherload -5` — automated in one `make.sh` for a ~3-second edit-build-run loop, with the Matrix Mode Monitor (MEGA+TAB) for debugging.

[[files.mega65.org]] is the official software distribution point — games, demos, utilities, ROMs, cores, manuals, and owner articles — browsed live rather than statically captured, with account-gated downloads and owner-only ROMs.

[[mega65.atlassian.net]] is the collaborative Confluence wiki: BASIC 65 how-tos, compatible hardware, system development notes, and the canonical release notes (0.97 "10th Anniversary Edition" and the 0.97.2 R6A bugfix release as of early 2026); its Ethernet-tools and petcat pages back the workflows described by [[wiebow.mega65.com]] and [[dansanderson.com]].

[[MEGA65-mega65-user-guide]] is the wiki's authority layer: the LaTeX source of all five official books in one repo, kept here as a full local clone so the entire spec is greppable — 45GS02 instruction set, VIC-IV/SID/Ethernet/CIA register appendices, memory map, hypervisor calls, KERNAL jump table, and the complete BASIC 65 keyword reference. For any official-spec question, grep these `.tex` files before searching the web.

[[RetroCogs-Mega65Tutorials]] turns [[retrocogs.mega65.com]]'s register lessons into a runnable 15-step curriculum — from blank skeleton through screens, scrolling, FCM/NCM, and progressively advanced RRB pixie engines — with a reusable `mega65system.asm`/`mega65macros.asm` library and a PNG→chr/pal asset pipeline, all in Kick Assembler.

[[MEGA65-mega65-tools]] is the official PC-side tool suite: `m65` (hardware swiss-army knife), `mega65_ftp` (SD card transfer), `etherload` (Ethernet deploy, beta), `coretool` (core container files), and `romdiff` (ROM patches) — prebuilt on the Filehost for all three OSes, source actively developed on the `development` branch.

[[MEGA65-mega65-code-snippets]] is the official meta-repo mapping the community GitHub ecosystem: assemblers (BSA, S65 macro toolkit), IDEs (C64Studio, on-device Eleven), third-party toolchains (m65dbg, MEGA65-SDK), example repos, complete games (raycaster, dragonrock, megafighter), and the MiSTer2MEGA65 core-porting framework — the "has someone already built X" index.

[[dansanderson-easyasm65]] covers the on-device path: EasyAsm assembles all 45GS02 instructions with Acme-compatible syntax inside the MEGA65's own screen editor (`MOUNT "EASYASM.D81" : BOOT`, Edit mode, Help-key menu), assembling to memory or disk — its README, embedded in full in the raw capture, is the complete manual.

[[lgblgblgb-xemu]] is the de-facto MEGA65 emulator (SDL2, GPL-2.0, master/next/dev branches) at the center of every workflow here, and [[MEGA65-mega65-core]] is the VHDL source of the machine itself — release 0.97.2 — tracked at brief detail for release/flashing questions, with builder.mega65.org doing automated builds.

[[dansanderson-mega65-symbols]] provides ready-to-include I/O register symbol files for six toolchains (ACME, Kick Assembler, ca65, cc65, Ophis, Rust), generated from `iomap.txt` in the MEGA65 core's VHDL — so register names track real hardware. Including the file for your toolchain at project start eliminates raw `$D0xx` address lookups throughout your source code.

[[MEGA65-mega65-rom-public]] is the public issue tracker and CHANGELOG for the closed-source MEGA65 ROM. The repository has no ROM source code, but its `CHANGELOG.md` is the authoritative version history — the definitive answer to "which ROM version introduced BASIC 65 feature X?" covering releases from 920287 (Jan 2022) through the current stable 920413 (v0.97, April 2025).

[[commodore-65-wikipedia]] provides the historical and hardware-spec baseline for the Commodore 65 prototype (C64DX) that the MEGA65 recreates: CSG 4510 @ 3.54 MHz, VIC-III, dual SID, BASIC 10.0, cancelled 1991. Useful when a MEGA65 register or mode traces back to the original C65 design — for the MEGA65's own implementation see [[MEGA65-mega65-core]] and [[MEGA65-mega65-user-guide]].

[[MEGA65-m65dbg]] is the project's enhanced serial debugger — the step up from the built-in Matrix Mode Monitor when symbolic source-level tracing is needed. It adds symbolic debugging (Ophis/ACME/CC65 symbol maps), hardware breakpoints, step/step-over/finish, memory watch, disassembly with source listings, and PETSCII screenshots over a serial connection to real hardware or a Unix socket to [[lgblgblgb-xemu]]. Borrows FTP and hardware-interaction code directly from [[MEGA65-mega65-tools]].

[[dansanderson-dis65]] adds the reverse-engineering side of the MEGA65 toolchain: a tiny Python CLI that disassembles raw binaries or Commodore PRGs for 6502, 65C02, 65CE02, and 45GS02 targets, auto-detects BASIC 2 vs BASIC 65 load-address conventions, and can emit source shaped for ACME or Kick Assembler. It fits where [[dansanderson.com]] and [[wiebow.mega65.com]] leave off: after you have produced or captured a PRG, dis65 helps turn it back into readable source, while [[MEGA65-m65dbg]] stays focused on live symbolic/debugger sessions.
