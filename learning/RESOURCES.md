# MEGA65 Hardware & FPGA Resources

> High-trust only. Knowledge is drawn from here, not parametric guesses. Annotate every entry.

## Knowledge — MEGA65 specific (verified)

- [Local wiki](../wiki/index.md) + `../raw/github/...` captures
  The repo's curated knowledge base. **Start every lookup here** per `../AGENTS.md`. Use for: anything MEGA65.
- [MEGA65 User's Guide / Books — LaTeX source](../raw/github/MEGA65-mega65-user-guide/)
  The 5 official books, greppable. Use for: exact specs — memory map, VIC-IV/45GS02 registers, DOS.
- [mega65-core (GitHub)](https://github.com/MEGA65/mega65-core) — local: `../raw/github/MEGA65-mega65-core.md`
  The actual gateware (VHDL). Use for: how every "chip" is really implemented. The deep end-goal reading.
- [C65 Specifications](https://github.com/MEGA65/c65-specifications) — local: `../raw/github/MEGA65-c65-specifications.md`
  The C65 the MEGA65 descends from. Use for: lineage, original chip intent.
- [mega65-kbd-pcb (GitHub)](https://github.com/MEGA65/mega65-kbd-pcb) + [c65gs — Keyboard PCB Design](https://c65gs.blogspot.com/2022/10/mega65-mk-ii-keyboard-pcb-design.html)
  The R6 keyboard: six I2C IO expanders, no programmable logic. Use for: how today's keyboard
  is wired and read.
- [wiebow — MEGA65 Hardware System and Concepts](https://wiebow.mega65.com/2023/10/21/mega65-hardware-system-and-concepts/) — local: `../raw/web/wiebow.mega65.com/`
  Concise "five system layers" + FPGA roles. Use for: the board's mental model. Caution: some hardware
  details are dated — treat the R6 User's Guide as authoritative over this page for any specific count.
- [Dan Sanderson — Exploring MEGA65 hardware](https://dansanderson.com/mega65/exploring-hardware/)
  Friendly board walkthrough, but it's a **revision-history tour** (covers earlier layouts, not R6-specific).
  Use for: gentle orientation only. For any current-board hardware fact, the **User's Guide R6 appendix +
  TE0765-06 schematic are authoritative** — see [r6-fpga-count-verification](reference/r6-fpga-count-verification.md).
- [Video: "MiSTer2MEGA65 Explained" — Oliver Graf (18:52, 2022)](https://www.youtube.com/watch?v=9Ib7z64z9N4) *(transcript-verified)*
  First ~7 min: clearest spoken explanation of "what an FPGA really is" + MEGA65-as-core. Rest: porting MiSTer
  cores to MEGA65. Use for: the FPGA concept (Lesson 01/02) and, later, core-porting (the dev goal).
- [c65gs.blogspot.com](https://c65gs.blogspot.com/)
  Creator Paul Gardner-Stephen's dev blog. Use for: deep hardware/FPGA design notes, JTAG, board bring-up.
- [Trenz TE0765 mainboard](https://shop.trenz-electronic.de/en/TE0765-06-T001CK-MEGA65-highly-advanced-C64-and-C65-compatible-8-bit-computer)
  Production board (Xilinx Artix-7 200T). Use for: official hardware specs, what you actually buy.
- [MEGA65 documentation landing page](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21331992/) — local: `../raw/web/mega65.atlassian.net/`
  Official always-current docs hub. Use for: finding the authoritative manual/schematic links.

## Wisdom — Communities

- [MEGA65 Discord — #mega65](../resources.md) (server `719326990221574164`)
  The live community. **Searchable by the agent** via Playwright (see `../AGENTS.md`). Use for: questions
  not written down — hardware-revision quirks, "why does my board do X", current core status.
- MEGA65 Forum / filehost (links in `../resources.md`)
  Use for: longer-form troubleshooting threads.

## Gaps (drives future search — fill before the FPGA phase)

- **FPGA / digital-design fundamentals** — need 1 high-trust course/text bridging digital-logic → FPGA.
- **VHDL language** — need a trusted VHDL tutorial/reference (the mega65-core reading depends on it).
- **Xilinx Artix-7 + Vivado toolchain** — need the official AMD/Xilinx Artix-7 datasheet & Vivado getting-started.
- **MEGA65 schematics** — locate the official board schematic PDF (check files.mega65.org / mega65-core repo).
