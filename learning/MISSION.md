# Mission: MEGA65 Hardware & FPGA

## Why
I want to genuinely *understand the MEGA65 from the silicon up* — not as a user but as someone
who could one day read every line of the gateware, modify a core, and build my own hardware for it.
The endgame is fluency in the FPGA/VHDL that *is* the machine.

## Success looks like
- Draw the current (R6) MEGA65 board block diagram from memory (the Artix-7 and what surrounds it,
  each chip's job, every external port).
- Read a module of `mega65-core` VHDL and explain what it does, line by line — on the current (R6)
  machine, `mega65-core` is the **only** gateware codebase (one FPGA, one repo).
- Write and simulate a small VHDL module of my own (e.g. a simple peripheral or logic block).
- Understand how a real chip (e.g. VIC-IV or 45GS02) is realized as gateware, not silicon.
- Confidently flash/diagnose/upgrade my own machine.

## Path (conceptual → deep)
1. Hardware: the current (R6) board — the Artix-7, chips, peripherals, schematics. *(start here)*
2. The chips up close: 45GS02, VIC-IV, SID, 45E100.
3. Memory map, I/O registers, system architecture.
4. FPGA fundamentals → VHDL basics → reading `mega65-core` → writing my own gateware.

## Constraints
- Background: comfortable with **digital logic / electronics** (gates, registers, datasheets). New to HDL and 6502.
- Conceptual-first, then go deep — don't drown me in VHDL before I understand the architecture.
- **Current hardware only**: teach the R6 (2024+) production machine. Anything not on the R6 board is out.
- Self-paced, multi-session. Wiki-first per repo `AGENTS.md`, plus web + live MEGA65 Discord.

## Out of scope (deferred, not abandoned)
- Application/software development (BASIC 65, game/graphics coding) — that's the later half of the
  full HW→SW journey in [roadmap.md](./roadmap.md). Kept out of *this* mission to protect focus
  until the hardware/FPGA foundation is solid.
- **Anything not on the current R6 board** — explicitly ruled noise by the learner. Not taught, not
  referenced, not footnoted — every hardware statement is about R6.
