# Game of Life on the MEGA65, in BASIC

- URL: https://dansanderson.com/lab-notes/mega65-game-of-life/
- Published: July 20, 2022
- Fetched: 2026-06-11

## Overview

Conway's Game of Life in BASIC 65: iterative optimization showing how algorithm design matters more than micro-optimizations. Baseline: ~3.7 sec/generation; optimized: ~3.05 sec/generation.

## Implementation Strategy

- Uses screen memory directly at $0800 as the game board (formula: `$0800 + 80*R + C`).
- Row buffers: maintains two 80-byte buffers to update board in-place without full array copy.
- Rules: cell lives with 2–3 neighbors; dead cell with exactly 3 becomes alive.

## Optimization Results

| Approach | Time/Generation |
|---|---|
| Baseline (2D arrays) | 3.69s |
| Single-letter variables | 3.56s |
| Array flipping (two boards) | 3.74s (slower!) |
| Row buffers | 3.28s |
| Screen memory as board | ~3.05s |

Array flipping slowed the program — increased address calculation overhead. Row buffers won.

## Key Lesson

"BASIC in 40 MHz is a game changer." Performance gains came from algorithmic improvements, not code obfuscation (removing spaces, combining statements made no measurable difference).

## User Interaction

Final version allows drawing patterns with SHIFT+Q, then RETURN to start evolution. Displays timing information.
