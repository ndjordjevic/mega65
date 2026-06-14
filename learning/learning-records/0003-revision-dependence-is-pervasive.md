# Revision-dependence is pervasive: FPGA count AND Attic RAM vary by unit

A full accuracy audit of Lesson 01 (requested by the learner) found two more revision-flattened claims
*in the already-corrected lesson*:

1. **The keyboard Lattice CPLD exists on MK-I keyboards only.** The MK-II keyboard (Oct 2022 redesign,
   forced by the Lattice part's ~90-week chip-shortage lead time) uses six plain I2C IO-expander chips —
   no programmable logic. The core auto-detects MK-I vs MK-II. It is NOT publicly documented which keyboard
   shipped with which batch, so per-unit claims must stay qualified.
2. **"8 MB Attic RAM / HyperRAM" is the R3 description.** From R4 onward a 64 MiB SDRAM is the (larger,
   faster) Attic RAM, and the User's Guide says HyperRAM is "likely not populated" on production R4+ units.

Verified-correct in the same audit: 4× SID, 40 MHz (~40× C64), two SD slots (internal full-size + rear
microSD, one active at a time), external port list (stable across R4–R6), TE0765 board ID, 45E100.

Why it matters for future sessions:
- The two-vs-three FPGA fix was not a one-off; **every** hardware quantity (RAM size, chip presence,
  connector details) must be stated per-revision on this platform. Treat "which unit?" as a mandatory
  qualifier, same as units on a physical quantity.
- Lesson 01 now teaches this explicitly (the FPGA-count question is framed as revision-dependent, with
  the MEGA Info / freezer HELP check). Reinforce this habit in later lessons and quizzes.
- The learner's own unit/keyboard model is unknown — ask when it becomes relevant (e.g. before any
  flashing/hardware lesson).

Evidence: User's Guide target-specific appendix + configuring chapter greps; c65gs MK-II keyboard post;
mega65-kbd-pcb repo. Supersedes nothing — extends [[0002-scope-all-three-fpgas]].
