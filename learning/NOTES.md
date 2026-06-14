# Teaching Notes

## Workspace
- **Workspace root = this `learning/` folder** (not the repo root). All teach files live here:
  `MISSION.md`, `RESOURCES.md`, `lessons/`, `reference/`, `learning-records/`, this file.
- `roadmap.md` is the wider HW→SW overview; `MISSION.md` is the active driver.

## Learner preferences
- **Conceptual-first, then deep.** Don't front-load VHDL; build architecture intuition first.
- Background: solid **digital logic / electronics**. New to HDL and 6502 — pitch above absolute-beginner
  on logic/circuits, but introduce HDL and 6502 concepts from scratch.
- End goal is real fluency: read every line of mega65-core VHDL, write his own gateware.
- Likes grounded, cited material — wiki-first, then web + live Discord. Not verbose; main points.

## Sourcing doctrine (repo-specific)
- Follow `../AGENTS.md`: local wiki → User's Guide grep → web → live Discord search.
- When a lesson surfaces a genuinely new high-quality source, queue it: `/pin-llm-wiki queue <url>`.

## Accuracy discipline (hard rule — see AGENTS.md)
- Cite every load-bearing claim; if unsourced, drop it or mark "to verify". No parametric guesses.
- For hardware/spec facts, grep the User's Guide / official docs BEFORE trusting a web summary.
- **Every hardware fact is about R6 — tie it to the R6 board / User's Guide before stating it.** Grep the
  User's Guide rather than trusting a web summary (web summaries blend board revisions and get R6 wrong).
- Separate verified fact from pedagogical framing/opinion.
- Corroborate central or shaky claims with a 2nd source; not blanket triple-search.

## Hardware baseline (user decision, 2026-06-12)
- **Teach the current production machine only: R6 (2024+).** Every hardware statement means R6. The user
  ruled all earlier hardware "noise" — do **not** mention it anywhere in lessons, references, or roadmap,
  not even as a "decode older docs" aside.
- If the user ever mentions owning a different unit, revisit (MEGA Info via freeze → HELP reports the revision).

## Next lesson candidate
- `0002` — "What an FPGA really is": gates/flip-flops → configurable logic → why MEGA65 uses one.
  (`0001` "What a MEGA65 physically is" is done: one-FPGA board diagram + each chip's job + ports.)
