# robotfindskitten, part 1

- URL: https://dansanderson.com/mega65/robot-finds-kitten/
- Published: October 12, 2023
- Fetched: 2026-06-11

## Overview

BASIC 65 coding exercise: implementing "robotfindskitten" (a zen simulation game) on the MEGA65. Part 1 covers game concept, key programming techniques, and suggested architecture.

## Game Concept

Based on Leonard Richardson's 1997 original. Screen shows robot, kitten, and non-kitten items (NKIs) with descriptions. Player navigates robot with cursor keys or joystick to find the kitten.

## Key BASIC 65 Techniques

**Display**:
- `SCNCLR` — clear screen
- `COLOR`, `BORDER`, `BACKGROUND` — set colors
- `CURSOR col,row` — position output
- `T@&(col,row) = screencode` — plot character
- `C@&(col,row) = color` — set color

**Input**:
- `GET` / `GETKEY` — keyboard input
- `JOY()` — joystick (values 0–8 for directions; +128 for fire)

**Randomization**:
```basic
INT(RND(1)*range)+offset   : REM random int in range
```

**Data**:
```basic
DATA "description1","description2",...
READ A$
RESTORE n   : REM reset read pointer to line n
```

## Program Structure

Four phases:
1. Introduction with keypress
2. Initialization (item + robot placement)
3. Game loop (input + collision)
4. Ending animation

NKI descriptions form a fifth data section. Test each phase with `RUN linenumber`.

## Note

New hardware keyboard scanner released alongside this article — improves typing responsiveness.
