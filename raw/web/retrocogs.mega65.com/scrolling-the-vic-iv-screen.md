# Scrolling the VIC-IV Screen

- URL: https://retrocogs.mega65.com/2022/10/04/scrolling-the-vic-iv-screen/
- Published: 2022-10-04
- Fetched: 2026-06-11
- Companion code: github.com/RetroCogs/Mega65Tutorials — `tutorial_2_scrolling.asm`
- Demo video: https://www.youtube.com/watch?v=5B7Pnj_YAQI

To scroll in all directions the simplest method is to set the screen and color buffers larger than the screen, then modify TEXTXPOS, TEXTYPOS, the screen pointer, and the color pointer.

## How the screen is sized and placed in memory

Recap of layout registers plus two new pointers:

- **CHRCOUNT** = characters per line the VIC-IV draws.
- **DISPROWS** = rows the VIC-IV draws.
- **LINESTEP** = bytes to advance per row.
- **SCRNPTR** = 32-bit screen RAM pointer with byte granularity — scroll one char left by adding one byte.
- **COLPTR** = color RAM as a 16-bit offset from $FF80000 (so the color buffer can be at most 64K).

Tip: keep every buffer from crossing a 64K boundary; then the upper 16 bits of the 32-bit address never change and moving to the next line is just a 16-bit add. When updating the screen pointer you really only need to update **$D060/$D061**.

## Horizontal scrolling

Set LINESTEP greater than CHRCOUNT (e.g. two 80-column screens wide = LINESTEP 160). Hold the scroll position in XPos; each frame subtract it from LEFT_BORDER to make the new TEXTXPOS. As XPos increases, TEXTXPOS moves left until a whole character has scrolled, then TEXTXPOS resets to LEFT_BORDER and you increment the screen/color pointers. Add 1 to CHRCOUNT (draw 81 chars) so no gap appears on the right as you scroll.

```
HShiftOffset H640 = (XPos & 7) * (H320 ? 2 : 1)
TEXTXPOS     H640 = LEFT_BORDER H640 - HShiftOffset H640
SCRNPTR(lohi)     = XPos / 8
COLPTR(lohi)      = XPos / 8
```

Updating TEXTXPOS and the pointers every frame takes about 1/8 of a raster line — very fast.

## Vertical scrolling

Same idea: subtract YPos from TOP_BORDER V400 into TEXTYPOS V400; when a full character has scrolled, add LINECOUNT to the pointers. Add 1 to DISPROWS so no gap shows at the bottom.

```
VShiftOffset V400 = (YPos & 7) * (V200 ? 2 : 1)
TEXTYPOS     V400 = TOP_BORDER V400 - VShiftOffset V400
SCRNPTR(lohi)     = (XPos / 8) + ((YPos / 8) * LINESTEP)
COLPTR(lohi)      = (XPos / 8) + ((YPos / 8) * LINESTEP)
```

Tip: pick vertical step values that are easy to compute (powers of two, or shift+add e.g. 160 = (Yc<<7)+(Yc<<5)). The sample uses a table of row offsets, fine for small scroll ranges.

## Vertical limitations

The new TEXTYPOS must always be >= 0, so the number of vertical scroll lines is limited; the sample includes error validation to catch a screen set too tall. Extend the technique to your game's buffer sizes and LINESTEP. The next tutorial covers handling NTSC vs PAL automatically instead of hardcoding one.
