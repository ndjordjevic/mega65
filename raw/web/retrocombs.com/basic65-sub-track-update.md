# An Update: The Submarine Tracking System conversion to BASIC 65

- URL: https://retrocombs.com/basic65-sub-track-update
- Published: 2022-03-28
- Fetched: 2026-06-11

## Overview

Updates the C128→MEGA65 submarine-tracking BASIC port using newly available BASIC 65 features for a near-exact replica of the original radar animation. Introduces a custom circle-drawing "Combs Flag."

## Key Technical Content

- Commands: `BOX`, `CIRCLE`, `LINE`, `SPEED`, `SLEEP`, `SOUND`, `CHAR`, `PEN`, `DOT`, `ELLIPSE`
- BASIC 65 is not "BASIC 10" but a heavily modified BASIC (~30 new commands, ~40% optimized)
- "Combs Flag" parameter (value `4`) draws circles starting at 270° clockwise (Commodore-standard behavior)
- Blip rendering: replaced C128 `DRAW` with BASIC 65 `LINE`
- `SPEED 1` ≈ C128's ~2 MHz; `{uloff}` control code removes underline
- Hardware: MEGA65 with 1581 disk / disk image
