# Auditing for accuracy means checking the cited sources, not just the prose

When the learner asked to "revise everything" for R6-only, the first pass only removed legacy *words*
from the visible body text (grep for "MAX10", "older docs", etc.). That missed the real problem: the
lesson's **primary source** (Dan Sanderson — "Exploring MEGA65 hardware") and **footnote 1** still pointed
at a page that describes the pre-R4 layout ("Artix-7 + MAX10 + Lattice chip", "8 MB Attic RAM") — and the
card even claimed "everything in this lesson is drawn from it", which was false after the R6 corrections.
The learner caught it, twice, and was rightly frustrated.

Why it matters for future sessions:
- **A keyword grep of the prose is not an accuracy audit.** A lesson can read as clean R6 while its
  *citations* propagate the exact error. Always re-open each cited source and confirm it supports the R6
  claim it's attached to.
- **Match the source to the claim type** (per AGENTS.md): load-bearing hardware facts (FPGA count, RAM,
  ports) must cite the **User's Guide R6 appendix + the TE0765-06 schematic** (verified in
  [[r6-fpga-count-verification]]) — never a community blog/video that blends board revisions.
- Community/web pages (dansanderson exploring-hardware, wiebow hardware-concepts) are revision-history
  tours; demote them to "gentle orientation", and never let them be the cited authority for a current
  spec.
- Concept-only sources (the Oliver Graf video's first ~7 min: "what an FPGA is") are revision-independent
  and fine to keep — the test is whether the cited portion makes a *board-spec* claim.

Evidence: in-session correction; the lesson's primary-source card + footnotes 1 and 4 were re-pointed from
dansanderson/wiebow to the User's Guide + schematic.
