---
type: source
source_url: https://mega65.org/
tags: [mega65, commodore-65, fpga-retro-computer, xemu-emulator, basic-65, alternative-cores, official-documentation]
related: [dansanderson.com, files.mega65.org, mega65.atlassian.net, lgblgblgb-xemu, MEGA65-mega65-core, MEGA65-mega65-user-guide, m-e-g-a.org]
product: mega65
detail_level: deep
created: 2026-06-10
updated: 2026-06-10
---

The official website of the MEGA65, a 21st-century FPGA realization of the never-released Commodore 65, built by MEGA Museum of Electronic Games & Art e.V. and manufactured with Trenz Electronic. The site is the canonical entry point to the entire MEGA65 universe: it links the four official PDF manuals, the Confluence documentation wiki, the Filehost software repository, the Xemu emulator path for the curious, the alternative-cores catalog, and every community channel. For this wiki it anchors the official vocabulary — what the machine is, what it ships with, and where each kind of authoritative information lives.

_All claims below are sourced from ../../raw/web/mega65.org.md unless otherwise noted._

## What it does

The MEGA65 is marketed as "a 21st century realization of the C65" — a real 8-bit computer (explicitly not an emulator) running around 40x faster than a C64 while staying highly compatible with both the C64 and C65. The hardware is completely open-source and includes a mechanical keyboard, HD video output, dual SD card slots, Ethernet, and a built-in floppy drive. The system software comprises the MEGA-OS hypervisor and BASIC 65, with a freezer, VFAT32 file system, 4 SIDs, and GEOS 65.

## Key features

- **Official PDF manuals** (free, rebuilt by Jenkins from latest source): the User's Guide (intro + condensed BASIC 65 reference), the BASIC 65 Reference (every command, function, operator), the Developer's Guide (writing programs for the MEGA65), and the Complete Compendium aka "The MEGA65 Book" — all volumes in one searchable PDF, 1,433 pages and growing.
- **Try-before-you-buy emulator path**: the `/try` guide walks through installing Xemu (stable `master` for most users, `next` for the latest ALL_INTROS), sourcing a ROM (licensing makes this tricky — MakeROM scripts patch a C65 ROM into a MEGA65 ROM), and running software via drag-and-drop, context menu, or `-hdosvirt` HDOS virtualisation (`DLOAD "FILE.PRG",U12`, `MOUNT "MYDISK.D81"`, `BOOT` for autoboot disks).
- **ALL_INTROS package**: one zip with every intro disk — about 263 community software titles as of 2025 — runnable in Xemu via the hdos folder; public edition for everyone, private edition (with ROMs) for registered owners.
- **Alternative cores**: because the machine is FPGA-based, its 7 core slots can be reflashed to become entirely different hardware (home computers, arcade boards, game consoles) — FPGA recreation, not software emulation, with timing far closer to original hardware. No promises on future cores: all core development is volunteer labor.

## Architecture and concepts

The FPGA is the architectural centerpiece: "programmable hardware" that runs code as if it *is* the recreated CPU, as opposed to an emulator translating instructions. The official MEGA65 core is the supported product; alternative cores are community-maintained and can be flashed into slots 1–7. Documentation is deliberately multi-home: PDFs (authoritative specs), the Confluence wiki (collaborative articles), Filehost articles (single-owner write-ups), and Dan Sanderson's Welcome Guide and Digest (curated onboarding and news).

## Main APIs

Not an API site, but the canonical entry URLs matter: `mega65.org/docs` (documentation landing), `mega65.org/try` (emulator guide), `mega65.org/chat` (Discord), `mega65.org/forum` (Forum64), `files.mega65.org` (software/ROMs/manuals), `cores.mega65.org` (alternative cores), `builder.mega65.org` (Jenkins PDF builds), plus code samples at github.com/MEGA65/mega65-examples and a German-language BASIC 65 Referenzhandbuch at 65site.de.

## When to use

Start here for anything official: buying (Trenz shop links), downloading manuals, first emulator setup, or finding the right community channel for a question. The docs landing page is the authoritative map of where each kind of MEGA65 documentation lives.

## Ecosystem

The site links outward to the whole ecosystem this wiki ingests separately: the MEGA65 GitHub org, Xemu, the Filehost, the Confluence wiki, retroCombs' video User's Guide series (six chapters mapped to User's Guide chapters), Dan's Welcome Guide and Digest, Paul Gardner-Stephen's development blog, and the Discord/Forum64/Reddit/YouTube community channels. Hardware is sold by Trenz Electronic (full product or separate parts).
