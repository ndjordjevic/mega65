---
type: source
source_url: https://github.com/MEGA65/mega65-weeip
tags: [tcp-ip, ethernet, networking, dhcp, dns, http, petscii-terminal, cc65, weeip]
related: [MEGA65-mega65-libc, MEGA65-mega65-tools]
product: mega65-weeip
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**mega65-weeip** is the official port of the WeeIP micro TCP/IP stack to the MEGA65's 100Mbit Ethernet controller. It enables the MEGA65 to participate in TCP/IP networks with DHCP, DNS, TCP, and UDP support — opening the door to BBS connectivity, HTTP downloads, and networked applications from a physical MEGA65.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-weeip.md unless otherwise noted._

## What it does

Provides a lightweight TCP/IP stack for the MEGA65:
- TCP and UDP protocols (client and server)
- ARP address resolution
- DHCP client for automatic IP configuration
- DNS client for hostname resolution
- Multiple socket support

Two example programs included:
- **haustierbegriff** — PETSCII terminal for connecting to BBSs
- **fetch** — simple HTTP file fetcher (see FETCH.md)

## Installation

Build with `make` (UNIX, CC65 required). The project uses CC65 and submodules: `mega65-tools` (for transfer utilities) and `cc65` (bundled).

## Key features

- Fixed checksum calculation bug from the original WeeIP
- Adapted for CC65 cross-compilation
- Event-driven design for easy integration into MEGA65 programs
- PETSCII-aware terminal application included

## Architecture

`src/` — WeeIP stack (TCP, UDP, ARP, DHCP, DNS) plus example programs. `include/` — headers. Based on WeeIP v1.0.3 by Bruno Basseto (C)1996-2014, MIT license. Changes copyright Paul Gardner-Stephen 2020-2022.

## Example usage

```sh
# Build all examples
make

# See FETCH.md for the HTTP fetch example usage
```

## Maintenance status

12 stars, 8 forks, MIT license, last pushed 2025-11-02. Explicitly noted as "work in progress, not yet usable." The PETSCII terminal (haustierbegriff) is further along than the HTTP fetch example.

## Ecosystem

Extends the MEGA65 beyond standalone retro computing to networked applications. Depends on CC65; could build on [[MEGA65-mega65-libc]] APIs once the library and stack are integrated. The [[MEGA65-mega65-tools]] submodule provides file transfer utilities used during development.
