Status: superseded by 0004

# Mission widened: understand the gateware of ALL three FPGAs, not just the Artix-7

During Lesson 01 the learner pushed back on a claim that "only the Artix-7 matters" for the VHDL journey.
He explicitly wants to understand the code running in the two helper FPGAs too — the **Altera MAX10**
(board housekeeping) and the **Lattice** keyboard chip — not only the main `mega65-core`.

Why it matters for future sessions:
- Treat the helper FPGAs as in-scope study targets, not footnotes. Plan a dedicated lesson on them.
- Reinforces that this learner wants *completeness/depth*, not the shortest path to the main core. Don't
  prune "peripheral" hardware as irrelevant — he wants the whole board.
- Practical consequence: he'll meet **three toolchains** (Vivado / Quartus / Lattice Diamond) and three repos
  (`mega65-core`, `mega65-r2-max10`, keyboard CPLD). Surface that when the FPGA-tooling phase arrives.
- Nuance to carry: the MAX10 is being removed on R5/R6 boards — studying it is partly studying a legacy helper.

Mission updated accordingly (see [[MISSION.md]] — added an all-three-FPGAs success criterion).
Evidence: direct user correction in-session.
