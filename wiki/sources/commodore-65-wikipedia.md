---
type: source
source_url: https://en.wikipedia.org/wiki/Commodore_65
tags: [commodore-65, c64dx, history, vic-iii, csg-4510, sid, prototype, hardware-specs, background]
related: [dansanderson.com, mega65.org, MEGA65-mega65-core, MEGA65-c65-specifications]
product: commodore-65
detail_level: standard
created: 2026-06-11
updated: 2026-06-12
---

Encyclopedia background on the **Commodore 65** (C64DX) — the 1990–91 prototype successor to the C64 that the **MEGA65 recreates in FPGA**. Useful as the historical/spec baseline: when a MEGA65 register, mode, or BASIC feature traces back to "the original C65," this is the reference for what that machine actually was. For the MEGA65's own implementation, see [[MEGA65-mega65-core]] and the official docs; for community history with more colour, [[dansanderson.com]] (chicagoland, first-ten-years).

_All claims below are sourced from ../../raw/web/commodore-65-wikipedia.md unless otherwise noted._

## Key specs (the C65 the MEGA65 emulates)

- **CPU:** CSG 4510 R3 (65CE02 derivative) @ **3.54 MHz**, 1 MB addressable
- **RAM:** 128 KB (expandable to 8 MB); **ROM** 128 KB
- **Graphics:** VIC-III (CSG 4567 R5) — 4,096-color palette, modes up to 1280×400; bitplanes, genlock, DMA/blitter; all VIC-II modes
- **Audio:** two CSG 8580R5 SID chips, stereo
- **Storage:** internal 3.5" 880 KB floppy, C1581-compatible
- **OS:** Commodore BASIC 10.0

## History in one paragraph

Conceived 1990 by Fred Bowen et al.; cancelled 1991 by Irving Gould amid falling C64 sales and Nintendo's rise. ~50–2,000 prototypes leaked to the market after Commodore's 1994 liquidation. The MEGA65 project (announced 2015, Museum of Electronic Games & Art) brought the design back as modern FPGA hardware.

## When to use

For the historical and original-hardware context behind MEGA65 features (why "C65 mode," why VIC-III/VIC-IV, the 4510/45GS02 lineage, dual SIDs). It's general background — for authoritative MEGA65 register/keyword detail use the official references in [[MEGA65-mega65-user-guide]].

## Ecosystem

Background reference linked from [[dansanderson.com]]'s intro. The MEGA65 implements this design: [[MEGA65-mega65-core]] (FPGA), [[mega65.org]] (project), [[MEGA65-mega65-rom-public]] (ROM history).
