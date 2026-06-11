# Converting a Commodore 128 Submarine Tracking System BASIC Program to the MEGA65

- URL: https://retrocombs.com/sub-track-sys
- Published: 2022-03-07
- Fetched: 2026-06-11

## Overview

Converts a C128 submarine-tracking BASIC program to the MEGA65, revealing the substantial differences between BASIC v7 and BASIC 65 that required significant code changes.

## Key Technical Content

- Commands: `GRAPHIC CLR`, `SCREEN`, `BOX`, `CHAR`, `PEN`, `CIRCLE`, `ELLIPSE`, `SOUND`, `SPEED`, `SLEEP`, `DO`/`LOOP`
- Graphics: 320×200 and 640×400 resolutions, color management, circle algorithms, character placement
- Three-section structure: screen init, sonar visualization, tracking logic (nested loops)
- Tools: MEGA65 Dev Kit, VICE (C128), MEGA65 Book
- ~40% code-length reduction; sprites noted for future enhancement
- Version differences: V7 uses separate H/V circle radii; BASIC 65 streamlines circle commands and adds text-direction/charset params
