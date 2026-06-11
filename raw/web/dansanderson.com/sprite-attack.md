# Sprite Attack!

- URL: https://dansanderson.com/mega65/sprite-attack/
- Published: February 15, 2024
- Fetched: 2026-06-11

## Overview

VIC-II hardware sprites on the MEGA65: BASIC 65 sprite commands, collision detection, SpritEd editor, animation, and a complete arcade game implementation.

## Basic Sprite Commands

```basic
SPRITE 0,1               : REM enable sprite 0
MOVSPR 0,160,120         : REM position at x=160,y=120
SPRITE 0,,2              : REM set color to palette entry 2
PALETTE COLOR 2,12,15,4  : REM set palette entry 2 to RGB(12,15,4)
```

## Multicolor Mode

```basic
SPRITE 0,,,,,,1   : REM enable multicolor
SPRCOLOR 4,5      : REM shared multicolor registers
```

Half-width (12px) with 2 additional shared colors across all multicolor sprites.

## Scaling

```basic
SPRITE 0,,,,1,1   : REM double width + height
```

## Movement

```basic
MOVSPR 0,+20,-10              : REM relative
MOVSPR 0,100,100 TO 250,200,5 : REM animated to target
MOVSPR 0,135#1                : REM continuous movement at angle
X=RSPPOS(0,0) : Y=RSPPOS(0,1) : SPEED=RSPPOS(0,2)  : REM query
```

## Collision Detection

```basic
COLLISION 2,220    : REM sprite-to-background collision → goto 220
```

`BUMP()` identifies which sprites collided.

## SpritEd (in Freezer menu)

- P: pixels, L: lines, X: boxes, Shift+X: filled boxes
- Space: draw, Del: erase, Ctrl+N: clear, +/−: cycle colors
- H/V: toggle expansion preview, F11: save, F3: return to BASIC

## Animation via String Variables

```basic
SPRSAV 2,C$    : REM copy sprite 2 to string
SPRSAV C$,5   : REM copy string to sprite 5
```

## Notes

- VIC-IV supports advanced sprite features (full-color mode, variable heights, 640px coordinates) not yet exposed by BASIC 65.
- Sprite-to-bitmap collision has a known bug; sprite-to-sprite and sprite-to-text work reliably.
