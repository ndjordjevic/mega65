# Focus narrowed: current production hardware only (R6, MK-II keyboard)

The learner explicitly ruled legacy hardware "noise": teach the **R6 board (2024+ production)** with the
**MK-II keyboard**. This supersedes [[0002-scope-all-three-fpgas]] (which had widened scope to the MAX10
and MK-I Lattice CPLD gateware — both absent from current machines).

Why it matters for future sessions:
- Baseline assumption in every lesson: **one FPGA (Artix-7), one gateware repo (`mega65-core`), one
  toolchain (Vivado), 64 MiB SDRAM Attic RAM, MK-II keyboard via I2C expanders.** Unqualified statements
  mean R6.
- Legacy details (MAX10, MK-I CPLD, HyperRAM) appear only as brief "older docs may say…" notes when needed
  to decode older sources — never as parallel content.
- This *simplifies* the mission: the entire gateware journey targets a single codebase.
- The revision-qualifier discipline (learning record 0003) still stands — it's what makes "R6 only" a
  precise statement rather than an accident.

Evidence: direct user instruction ("focus on the latest board… 2022 boards are just noise").
