---
type: source
source_url: https://wiebow.mega65.com/
tags: [cross-development, kick-assembler-45gs02, etherload, mega65-ftp, c1541-d81, xemu, matrix-mode-debugger, build-automation, fpga, hyppo, freezer, system-architecture]
related: [dansanderson.com, retrocogs.mega65.com, mega65.atlassian.net, RetroCogs-Mega65Tutorials, MEGA65-mega65-tools, lgblgblgb-xemu, dansanderson-dis65]
product: wiebow
detail_level: standard
created: 2026-06-10
updated: 2026-06-12
---

Wiebo de Wit's MEGA65 blog — a small (3-post), now-dormant blog whose standout is a **complete, copy-pasteable Linux cross-development pipeline** (Dec 2023): assemble 45GS02 code with the Kick Assembler 65CE02 fork, build a D81 with `c1541`, and deploy to both Xemu and a real MEGA65 over Ethernet — all from one `make.sh` (Ctrl-B in Sublime), with a verified **3.3-second** edit-build-run loop. The most concrete build recipe in this wiki; its Ethernet-deployment specifics (the `etherload -5` reboot flag, IPv6 link-local) aren't spelled out elsewhere. Also a clean layered-architecture overview for newcomers. Complements the broader tool survey in [[dansanderson.com]] (cross-development-1/2) and the graphics focus of [[retrocogs.mega65.com]].

**How to use this page:** the table is an index — each row links to a raw page under `../../raw/web/wiebow.mega65.com/`. The cross-development page is a **near-verbatim capture** (full commands, `make.sh`, and test code) since the exact invocations are the value; the `- URL:` at the top of each raw page is the original. Answer chain: this index → raw page → original URL.

_All claims below are sourced from ../../raw/web/wiebow.mega65.com/ unless otherwise noted._

---

## Posts (all 3, newest first)

| Date | Article | Summary |
|---|---|---|
| 2023-12-31 | [cross-development.md](../../raw/web/wiebow.mega65.com/cross-development.md) | The full Linux cross-dev pipeline: Kick Assembler 65CE02 fork (`.cpu _45gs02`), `c1541` for D81, Xemu, Sublime + 45GS02 syntax, Ethernet deploy via `mega65_ftp -e` + `etherload -5` (IPv6 link-local), complete `make.sh`, a BASIC-stub test program, Matrix Mode debugging. Concrete commands + code. |
| 2023-10-21 | [hardware-system-and-concepts.md](../../raw/web/wiebow.mega65.com/hardware-system-and-concepts.md) | The MEGA65's 5 layers (FPGA hardware → cores → HYPPO → ROM → software); the 3 FPGA chips (Artix-7, MAX10, Lattice); 8 core slots (NO SCROLL boot); Hypervisor + Freezer (RESTORE, MEGA Info via HELP); `MEGA65.ROM`. Good newcomer orientation. |
| 2023-10-15 | [the-mega-discovery.md](../../raw/web/wiebow.mega65.com/the-mega-discovery.md) | Intro post — the blog's scope and the author's project goals. No technical content. |

---

## When to use

The first thing to follow when **standing up your own assembly build pipeline**, especially for the Ethernet-deployment details (IPv6 link-local, the `-5` reboot flag) that other sources gloss over. For the layered hardware/HYPPO/Freezer concepts, the hardware post is a clean overview (cross-check against the official Chipset/Developer references in [[MEGA65-mega65-user-guide]]). Windows users: dirmaster and M65Connect for disk-image management.

## Ecosystem

References the Kick fork on GitLab (jespergravgaard), magic64knight.com, the official Confluence [Ethernet-tools page](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/29327361/) ([[mega65.atlassian.net]]), [[lgblgblgb-xemu]] (Xemu), and [[MEGA65-mega65-tools]] (`mega65_ftp`, `etherload`). Hosted on the community mega65.com subdomain family alongside [[retrocogs.mega65.com]].
