# MEGA65 Summer Filehost Roundup

- URL: https://dansanderson.com/mega65/2026-filehost-roundup/
- Published: October 17, 2026
- Fetched: 2026-10-18

## Overview

Roundup issue of Dan's MEGA65 Digest (no single feature article). Marks four years of the Digest, five years since the original MEGA65 pre-orders, and the 500th file uploaded to Filehost. Dan travelled to VCF West (California) and VCF Midwest (Illinois). Activity in software, alternate cores and genAI experiments outpaced his ability to test, so he summarizes announcements and uploads. Cores are not all tested by him; docs at cores.mega65.org.

## MEGA65 news

- **MEGASPUTM** (kibo, M3wP): LucasArts-style adventure engine now plays *Zak McKracken and the Alien Mindbenders*; uses Amiga-version data files via an included utility. User's Guide on branch `main-zak`; source on Codeberg. Builds on the earlier *Maniac Mansion* version.
- **Simon the Sorcerer** (wombat): ScummVM-based engine port, based on the Amiga CD32 version; on Filehost and GitHub `mlund/simon65`. User must supply the original Amiga CD32 game data.
- **Ozmoo Z-machine v6 support** (Fredrik Ramsberg, Johan Berntsson): Z6 adds graphics/sound (most Infocom games are v3/v5). Uploaded: Infocom Z6 bundle (*Arthur*, *Journey*, *Shogun*, *Zork Zero*), *Wyrmward* (Johan's original), *Vanyar* (port of Johan's 1986 game). Text-adventure background: Oct 2022 Digest.

## Filehost software and games

**Languages / tools / utilities**
- MyLISP65 (Fenix): LISP-1 interpreter, ported from Sinclair QL version; math packages (GitHub `dfernande132/MyLISP65`)
- Pascal65 (TwoBitRetro): on-device Pascal compiler + IDE, major recent improvements
- MegaPad (piramania): document editor, Markdown-compatible format, menus, mouse, multilingual chars/keyboard layouts
- KnockCSV (Frogboon): CSV columnar editor
- RTC Tool (Warlock): set date/time, identify RTC hardware model, NTP sync at boot
- BASIC Clock (fredrickr): clock + BASIC coding example
- Mega Adventure Creator (NeonKnight): BASIC 65 adventure toolkit, menus, NCM stills (GitHub `lipi650/MAC`)
- Net Tools (silent-command): SSH, FTP/SFTP, IRC, Gopher, telnet BBS client

**Games / demos**
- piramania: Quackout, Towering Rescue, Columns 65, LeMans, Labyrinth, MegaQix
- Chessoban (lochmana, Sokoban variant); dugout (bushnrvn, baseball-themed digging game); Search and Rescue (johan, voxel flight sim)

**Tiwaz genAI projects** (11 titles in 4 weeks): GOGOAstra, IONDRIFT, Rockstorm, NEON WARDEN, AstraAmp (SID player), SHIPYARD (small neural-net ship generator), TURTLE65, TINYBRAIN65 (tiny local text LLM demo running on the MEGA65), mesh65 (3D polygons), Space commander, Space particles.

## Alternate cores ("Summer of Cores")

| Core | Author | Status / notes |
|---|---|---|
| Amiga 500 (OCS) | sy2002 | Feature-complete V2 beta; stable soon; Kiwi continues after V2 |
| Commodore 64 | MJoergen, sy2002 | v6 alpha; second virtual drive; `.d64`/`.d81` |
| Megamiga (A1200) | johey | v0.3.0; uses R6 SDRAM for more RAM; OCS/ECS(A600)/AGA; **R6+ only** |
| Mega//e (Apple IIe) | muse5150 | v2 beta; better disk image support |
| Mega800 (Atari 800) | muse | v1.0 alpha |
| Black Tiger (arcade) | muse | new release |
| Elevator Action (arcade) | muse | updated builds for R3 and R6 |
| QL4M65 (Sinclair QL) | Fenix | v1.5 adds QXL.WIN HDD image; **R6 only** (v1.01 for R3) |
| CPC4MEGA65 (CPC 6128) | Fenix | v1.0; real CPC disks in physical floppy drive |
| MegaST (Atari ST) | Chris Freeman | hardware peripherals via PMOD headers |
| C128 | Stefan Eilers | v1.0 beta; virtual drives; Caps Lock = 40/80 column key |
| BIT90 | cf23 | from-scratch recreation; runs ColecoVision cartridges |
| IMSAI 8080 | toby01019 | experimental; on-screen lights/switches; built-in terminal |

## Paul's PicoPi-based core loader

MEGA65 has only eight core flash slots. Paul's PicoPi loader keeps cores on a separate SD card and loads them through the **JTAG port**, dumping a bitstream straight into the FPGA; the connector's **UART** pins let the MEGA65 browse/request bitstreams without a second computer. Paul's blog also covers the MEGAphone project.

## Closing notes

- "Featured Files" will be scaled back in favour of project news, feature articles and programming tutorials; a bonus issue is possible by end of October if a half-written article is finished.
- Staying current: **@mega65files** Mastodon bot (new Filehost uploads, also RSS); Discord announcements channel; Discord software-projects forum; Discord core channels/forum.
