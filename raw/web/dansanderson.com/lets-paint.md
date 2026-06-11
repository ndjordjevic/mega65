# Let's Paint!

- URL: https://dansanderson.com/mega65/lets-paint/
- Published: July 17, 2024
- Fetched: 2026-06-11

## Overview

Creating graphics with BASIC 65: bitmap screen setup, drawing commands, mathematical graphing, and an interactive paintbrush using keyboard, joystick, and mouse.

## Screen Initialization

```basic
SCREEN 0,320,200,5   : REM 320x200, 5-bit color depth (32 colors)
```

## Drawing Commands

```basic
PEN 1
LINE 20,30,300,180
DOT 4,4
BOX 180,10,240,50
CIRCLE 50,150,24
ELLIPSE 180,150,50,20
POLYGON 250,100,40,40,5
```

Coordinate system: X = horizontal from left, Y = vertical from top.

## Generative Art with Loops

```basic
FOR X=0 TO 319 STEP 20
  LINE X,0,X,199
NEXT X
PEN RND(1)*32
LINE RND(1)*320,RND(1)*200,RND(1)*320,RND(1)*200
```

## Graphing Calculator

Define function, scale to screen coordinates, draw axes, plot connected line segments:
```basic
1 DEF FN Y(X) = SIN(X*9)+1.5
2 XL = -3 : XH = 3 : YL = -1 : YH = 4
```

## Interactive Paintbrush

Keyboard:
```basic
GETKEY A$ : IF A$=CHR$(17) AND Y<199 THEN Y=Y+1
```

Joystick:
```basic
J=JOY(2) : IF (J=4 OR J=5 OR J=6) AND Y<199 THEN Y=Y+1
```

Mouse:
```basic
MOUSE ON,1
RMOUSE X,Y,B
IF B THEN DOT X-24,Y-50
```

Enhancements: sprite cursors, color selection, sound effects, mirror effects.
