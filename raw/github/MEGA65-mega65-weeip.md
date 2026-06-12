# MEGA65/mega65-weeip

## Metadata
- Stars: 12
- Primary language: C
- Default branch: master
- Latest release: none
- License: MIT License
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/mega65-weeip

## Description
Port of WeeIP TCP/IP stack to the MEGA65

## README
WeeIP for the MEGA65 — a port of the WeeIP micro TCP/IP stack (originally for PIC18 microcontrollers) to the MEGA65's 100mbit fast Ethernet controller. By Paul Gardner-Stephen.

**Features:**
- TCP and UDP protocols
- ARP address resolution
- Multiple socket support (client and server)
- DHCP client — automatic IP configuration
- DNS client — hostname resolution
- Lightweight, 8-bit-friendly design
- Event-driven pattern for easy integration

**Example programs:**
- `haustierbegriff` — PETSCII terminal for BBSs
- `fetch` — Simple HTTP file fetcher for MEGA65

**Build:** CC65-based; `make` on UNIX. Requires CC65 and MEGA65 toolchain.

**Status:** Work in progress, not yet fully usable. Several bug fixes over original WeeIP including a nasty checksum calculation bug. See `FETCH.md` for usage of the HTTP fetcher.

**Original:** WeeIP v1.0.3 by Bruno Basseto (C)1996-2014.

**Submodules:** cc65 and mega65-tools (as submodules via .gitmodules).

## Top-level structure
- dir src/ — C sources for WeeIP stack (TCP, UDP, ARP, DHCP, DNS) and example programs
- dir include/ — Header files
- dir assets/ — (data assets)
- file Makefile — build system
- file FETCH.md — HTTP fetch example documentation
- file INSTALL — installation notes
- file LICENSE — MIT
- file README — WeeIP stack description
- file run_graze — utility script
- file cc65 — CC65 submodule reference
- file mega65-tools — mega65-tools submodule reference
