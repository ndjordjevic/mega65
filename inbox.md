# Inbox

Drop URLs below under `## Pending`. Run `/pin-llm-wiki run <url>` to ingest a single URL (auto-queues it if missing), or `/pin-llm-wiki run` to batch-process every pending item. Agents may use `/pin-llm-wiki queue <url>` to suggest URLs without immediately ingesting them.

## Pending

<!-- Add URLs here, one per line, as markdown checkboxes.
     Supported inline tags (append each wrapped in HTML comment syntax):
       detail:brief        — override detail level for this source
       detail:standard
       detail:deep
       branch:dev          — GitHub: use this branch instead of default
       clone               — GitHub deep: full git clone to raw/github/<org>-<repo>/
       skip                — skip this URL on the next run
       companion:github.com/<org>/<repo>  — web: use this repo as companion (skip auto-discovery)
       no-companion        — web: suppress companion GitHub fetch even if a repo is found
       note: <text>        — freeform note for human review (ignored by ingest)
-->

<!-- Websites -->

<!-- GitHub repos -->

<!-- MEGA65 org — originals only (org forks skipped; upstream queued separately where noted) -->

<!-- YouTube: playlists are not ingestible — expand first, then queue picked videos here.
     yt-dlp --flat-playlist --print "https://www.youtube.com/watch?v=%(id)s  # %(title)s" "https://www.youtube.com/playlist?list=PLPehmjqZolWArdt53pl1QyJurZDu3oJKy"
     yt-dlp --flat-playlist --print "https://www.youtube.com/watch?v=%(id)s  # %(title)s" "https://www.youtube.com/playlist?list=PLRVBh2hjFTomDGwIT7uPMJv4zH9JAUSVG"
-->


## Completed

- [x] https://mega65.org/ <!-- detail:deep --> <!-- note: official site; companion discovery of mega65-core is desirable --> <!-- ingested 2026-06-10 -->
- [x] https://dansanderson.com/mega65/ <!-- detail:deep --> <!-- no-companion --> <!-- note: hub site; deep crawl must include /mega65/welcome/ (the Welcome Guide, best beginner doc) plus Digest and cross-dev series --> <!-- ingested 2026-06-10 -->
- [x] https://retrocombs.com/mega65 <!-- note: resource page + User's Guide chapter walkthroughs --> <!-- ingested 2026-06-10 -->
- [x] https://retrocogs.mega65.com/ <!-- note: 45GS02/VIC-IV coding tutorials blog --> <!-- ingested 2026-06-10 -->
- [x] https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/ <!-- note: cross-dev setup guide --> <!-- ingested 2026-06-10 -->
- [x] https://files.mega65.org/html/main.php <!-- detail:brief --> <!-- no-companion --> <!-- note: filehost; catalog only --> <!-- ingested 2026-06-10 -->
- [x] https://mega65.atlassian.net/wiki/spaces/MEGA65/overview <!-- detail:standard --> <!-- note: full page index via REST API; 9 sections, 66+ pages catalogued --> <!-- ingested 2026-06-10 --> <!-- refreshed 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-user-guide <!-- detail:deep --> <!-- clone --> <!-- note: LaTeX source of all 5 official books; the greppable spec --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/RetroCogs/Mega65Tutorials <!-- detail:standard --> <!-- clone --> <!-- note: 45GS02 assembly tutorials with code --> <!-- ingested 2026-06-10 --> <!-- refreshed 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-tools <!-- note: mega65_ftp, etherload, CLI dev tools --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/MEGA65/mega65-code-snippets <!-- note: meta-repo of example code --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/dansanderson/easyasm65 <!-- note: on-device assembler --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/lgblgblgb/xemu <!-- detail:brief --> <!-- note: emulator; usage docs only, skip internals --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/MEGA65/mega65-core <!-- detail:brief --> <!-- note: FPGA core; brief until hardware-level questions arise --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/MEGA65/m65dbg <!-- detail:standard --> <!-- note: symbolic debugger — breakpoints, step/step-over/finish, register display, memory watch, disassembly with source listings; supports Ophis/ACME/CC65 symbol maps; complements mega65-tools (transfer/flash/monitor) with source-level debugging --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/dansanderson/dis65 <!-- note: 6502/65C02/65CE02/45GS02 disassembler; PRG-aware, acme/kickass output; complements m65dbg and cross-dev workflow --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/dansanderson/tpn65 <!-- note: host-side BASIC 65 cross-transpiler (Eleven-like: labels, long names, optional line numbers); unique dev path not covered elsewhere in wiki --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/dansanderson/homebrew-mega65 <!-- detail:brief --> <!-- note: brew tap for mega65-m65connect + mega65-xemu on macOS; practical onboarding complement to retrocombs Xemu guides --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/dansanderson/joytest65 <!-- detail:brief --> <!-- note: joystick/paddle tester; documents CIA $DC00/$DC01 register bits and assembly read patterns --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/dansanderson/mega65-pcfonts <!-- detail:brief --> <!-- note: 43 Oldschool PC fonts converted to MEGA65 TCR format; documents Tall Character mode usage --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/cc65/cc65 <!-- note: official cc65 cross-compiler suite; cited in [[dansanderson.com]] cross-development series for MEGA65/C65 (Dan also maintains a personal fork with extra commits) --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/dansanderson/bf-mega65 <!-- detail:brief --> <!-- note: 45GS02 Brainf*ck interpreter example; already in resources.md --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/dansanderson/bsa-vscode <!-- detail:brief --> <!-- note: VS Code syntax/definitions for BSA assembler; pairs with upstream https://github.com/Edilbert/BSA (MEGA65/BSA is a fork) --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/RetroCogs/GameShell65 <!-- detail:brief --> <!-- note: Kick Assembler game framework (RRB-heavy, GameStates, Pixies, DMA-buffered frame loop); README has placeholder sections — 2 stars, niche, but shows real game architecture; natural next step after Mega65Tutorials --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/RetroCogs/GS65_ShmupExample <!-- detail:brief --> <!-- note: example shmup using GameShell65 framework; 0 stars, 14 commits; companion to GameShell65 if that is ingested --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MirageBD/MegaTool <!-- note: graphics conversion + cruncher utility (gfx2code, imgconvert, cruncher); no README — purpose inferred from source filenames; used by RetroCogs in their game dev workflow --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/lgblgblgb/megacyc <!-- note: 45GS02 opcode/cycle timing tester for real MEGA65 + Xemu; helps validate emulator CPU timing against hardware --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/lgblgblgb/mega80 <!-- note: CP/M v2.2 on MEGA65 via software i8080 emulation + custom CBIOS; D81 in dist/bin — unique platform experiment by Xemu author --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/lgblgblgb/mega65-utils <!-- note: LGB utility collection — mega65info (hardware query), m65c (cross-platform SD/file commander), navigator, eth-tool (early Ethernet/monitor UDP), c65izer; WIP but 6★, complements [[MEGA65-mega65-tools]] --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/lgblgblgb/c64-sfx-cartridge-player <!-- detail:brief --> <!-- note: AdLib/OPL2 DRO player for C64 SFX cartridge and MEGA65 (direct OPL register access); doubles as MEGA65 OPL hardware test --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/lgblgblgb/fdc65bas <!-- detail:brief --> <!-- note: BASIC65 floppy sector read via direct FDC POKE/PEEK; niche I/O learning example --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/eleven <!-- note: on-device BASIC 65 IDE/transpiler (labels, long names, build-to-PRG); maintained by Gurce; Confluence Eleven Walkthrough; pairs with tpn65 cross-transpiler --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/m65connect <!-- note: official Xojo GUI — SD card manager, PRG/bitstream/ROM transfer, terminal, remote keyboard, ROM configurator; complements [[MEGA65-mega65-tools]] --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-libc <!-- note: official C library for cc65 and llvm-mos; dependency of mega65-fdisk; fills C dev gap next to cc65/cc65 --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-weeip <!-- note: official WeeIP TCP/IP port — DHCP, DNS, PETSCII terminal, HTTP fetch; Ethernet networking on real hardware --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-examples <!-- note: official community example collection (per-topic dirs + build instructions); linked from [[mega65.org]] --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-freezemenu <!-- note: FREEZER.M65 + integrated SD utilities (MEGAINFO, CHARSET, slot freeze/restore); required on SD card for normal operation --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-fdisk <!-- note: SD-card FDISK+format utility; builds with mega65-libc + cc65 --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/open-roms <!-- note: unencumbered open-source C64/C65 ROM replacement project; initial focus includes MEGA65 --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/c65-specifications <!-- detail:brief --> <!-- note: updated Commodore C65/C64DX system specification; team corrections — background for [[commodore-65-wikipedia]] and register questions --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/MEGA65/mega-basic64 <!-- detail:brief --> <!-- note: experimental MEGA65-extended C64 BASIC 2 (256-colour text, tiles/canvases); team testbed, not shipping ROM --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/Edilbert/BSA <!-- note: upstream of MEGA65/BSA fork — Bit Shifter Assembler for 6502/65C02/45GS02; listed in [[MEGA65-mega65-code-snippets]] --> <!-- ingested 2026-06-12 -->
- [x] https://github.com/sy2002/MiSTer2MEGA65 <!-- ingested 2026-06-13 -->
- [x] https://github.com/MEGA65/mega65-kbd-pcb  <!-- note: MK-II keyboard PCB design — six I2C IO expanders (current R6 keyboard). Found during Lesson-01 accuracy audit. --> <!-- ingested 2026-06-13 -->
- [x] https://c65gs.blogspot.com/2022/10/mega65-mk-ii-keyboard-pcb-design.html  <!-- note: creator's MK-II keyboard redesign story (why the Lattice CPLD was dropped). Companion to mega65-kbd-pcb. --> <!-- ingested 2026-06-13 -->
- [x] https://www.youtube.com/watch?v=9Ib7z64z9N4  <!-- note: "MiSTer2MEGA65 Explained" (Oliver Graf, 18:52). First ~7 min = clearest spoken "what is an FPGA / MEGA65-as-core"; rest = porting MiSTer cores. Transcript-verified. --> <!-- ingested 2026-06-13 -->
- [x] https://www.m-e-g-a.org/  <!-- ingested 2026-06-13 --> <!-- updated 2026-06-13: added full blog index, all 117 posts via WP feed -->
- [x] https://c65gs.blogspot.com/ <!-- note: creator's dev blog — ingested as an INDEX of all 427 posts (title + 1-line gloss each) via Blogger feed API, not full-text. Single full post (MK-II keyboard) is [[c65gs-mk-ii-keyboard]]. --> <!-- ingested 2026-06-13 -->

<!-- Processed lines are moved here automatically.
     Format after ingest: - [x] https://... with an "ingested YYYY-MM-DD" HTML comment appended.
     To re-fetch: add a "refresh" HTML comment to the line, then run /pin-llm-wiki run.
     The refresh tag is removed automatically after re-fetch.
-->
