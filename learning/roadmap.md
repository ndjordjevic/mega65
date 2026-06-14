# MEGA65 Learning Roadmap — 10,000-meter view

> Goal: understand the MEGA65 end-to-end, **hardware → software**. Start at the board.
> Sources: local wiki first (`wiki/index.md`, `raw/github/...`), **plus web search** and live Discord — use all three freely for learning, not just for gaps.

## The arc (whole journey)

- **Phase 1 — Hardware** ← *start here*: board, FPGA, chips, peripherals, schematics.
- **Phase 2 — The chips up close**: 45GS02 CPU, VIC-IV video, SID audio, 45E100 ethernet.
- **Phase 3 — Memory & system**: memory map, banking, I/O registers, hypervisor.
- **Phase 4 — Firmware/OS**: MEGA-OS hypervisor, ROM, BASIC 65, freezer.
- **Phase 5 — Software dev**: BASIC 65 → assembly (45GS02) → C; toolchain + Xemu.
- **Phase 6 — Graphics/sound projects**: VIC-IV modes, RRB/pixies, SID music.

---

## Phase 1 — Hardware (first focus)

- **Big picture**: what physically *is* a MEGA65 — an FPGA recreating a C65-class machine, not discrete chips. Grasp "the chips are gateware (VHDL), the board hosts the FPGA + real I/O."
  - Sources: `resources.md` Hardware Reference; [[commodore-65-wikipedia]] for the C65 lineage; web: [Dan Sanderson — Exploring MEGA65 hardware](https://dansanderson.com/mega65/exploring-hardware/) (best beginner hardware tour).
- **The FPGA board**: the R6 board is Trenz **TE0765** with a **Xilinx Artix-7 200T** — the **only** FPGA on the machine; **Nexys A7** = hobbyist alt. Understand what an FPGA is and why MEGA65 uses one.
  - Sources: `raw/github/MEGA65-mega65-core.md` (the gateware), Trenz shop link in `resources.md`; web: [Trenz TE0765 mainboard](https://shop.trenz-electronic.de/en/TE0765-06-T001CK-MEGA65-highly-advanced-C64-and-C65-compatible-8-bit-computer), [c65gs.blogspot.com](https://c65gs.blogspot.com/) (creator Paul Gardner-Stephen's dev blog — deep hardware notes).
- **The mainboard & schematics**: locate and read the official schematics; identify power, clocking, connectors, FPGA pinout.
  - Action: find schematics via files.mega65.org / mega65-core repo (note exact location once found; queue to wiki).
- **On-board chips & peripherals**: CPU (45GS02), VIC-IV (HD video), 4×SID audio, 45E100 ethernet, dual SD slots, USB, IEC, cartridge/expansion port, joystick ports.
  - Sources: `raw/github/MEGA65-c65-specifications.md`, the User's Guide books in `raw/github/MEGA65-mega65-user-guide/`.
- **What can attach**: peripherals & expansion (SD cards, cartridges, IEC drives, monitors, networking).

**Phase 1 done when** I can sketch the block diagram from memory: FPGA at center, what each chip does, and every external port.

---

## Working method

- Wiki-first per `AGENTS.md`; grep the User's Guide LaTeX for exact specs.
- Live-search the MEGA65 Discord for things not written down (per `AGENTS.md`).
- Capture genuinely new findings back into the wiki (`/pin-llm-wiki queue`).
- Notes per phase go in this `learning/` folder (e.g. `learning/01-hardware.md`).
