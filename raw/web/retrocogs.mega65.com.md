# retrocogs.mega65.com

## Fetch log
- Inbox URL: https://retrocogs.mega65.com/
- Final URL: https://retrocogs.mega65.com/
- Fetched: 2026-06-10
- Pages: 6
- Mode: standard
- Note: WordPress blog "Coding for the Mega65" by RetroCogs. Captured: landing, tutorials category, and 4 core VIC-IV tutorial posts. Companion repo: github.com/RetroCogs/Mega65Tutorials (queued separately in this wiki, so no companion fetch here to avoid duplication).

## Landing page — https://retrocogs.mega65.com/

## [The VIC-IV Screen Layout](https://retrocogs.mega65.com/2022/09/20/the-vic-iv-screen-layout/)

•September 20, 2022•

With the addition of the VIC-IV, the Mega65 is not limited to a fixed sized screen anymore, the application can set the screen to any size up to…

## [VIC-IV graphics, using RRB for pixies](https://retrocogs.mega65.com/2025/08/14/vic-iv-graphics-using-rrb-for-pixies/)

Raster Rewrite Buffer The Raster Rewrite Buffer is a new feature introduced in the Mega65, you can think of it as a 2048 pixel wide single line buffer….

## [VIC-IV graphics, setting up FCM and NCM](https://retrocogs.mega65.com/2025/08/13/vic-iv-graphics-setting-up-fcm-and-ncm/)

NOTE this doc is in progress and images will be added Refresher on C64 background graphics Due to the Mega65’s graphics being an extension of previous hardware, let’s…

## [Scrolling the VIC-IV Screen](https://retrocogs.mega65.com/2022/10/04/scrolling-the-vic-iv-screen/)

Unless all the action on your game is going to take place on a single screen you are going to want to scroll the screen. Using the VIC-IV…

## [Welcome to a very Mega65 centric blog!](https://retrocogs.mega65.com/2022/09/12/hello-world/)

I’m currently working on a shmup for the Mega65 called FirstShot and while I’m procrastinating on the various challenges of making a game with 4 registers and limited…

## Tutorials category — https://retrocogs.mega65.com/category/tutorials/

## [VIC-IV graphics, using RRB for pixies](https://retrocogs.mega65.com/2025/08/14/vic-iv-graphics-using-rrb-for-pixies/)

•August 14, 2025•

Raster Rewrite Buffer The Raster Rewrite Buffer is a new feature introduced in the Mega65, you can think of it as a 2048 pixel wide single line buffer….

## [VIC-IV graphics, setting up FCM and NCM](https://retrocogs.mega65.com/2025/08/13/vic-iv-graphics-setting-up-fcm-and-ncm/)

NOTE this doc is in progress and images will be added Refresher on C64 background graphics Due to the Mega65’s graphics being an extension of previous hardware, let’s…

## [Scrolling the VIC-IV Screen](https://retrocogs.mega65.com/2022/10/04/scrolling-the-vic-iv-screen/)

Unless all the action on your game is going to take place on a single screen you are going to want to scroll the screen. Using the VIC-IV…

## [The VIC-IV Screen Layout](https://retrocogs.mega65.com/2022/09/20/the-vic-iv-screen-layout/)

With the addition of the VIC-IV, the Mega65 is not limited to a fixed sized screen anymore, the application can set the screen to any size up to…

## [Welcome to a very Mega65 centric blog!](https://retrocogs.mega65.com/2022/09/12/hello-world/)

I’m currently working on a shmup for the Mega65 called FirstShot and while I’m procrastinating on the various challenges of making a game with 4 registers and limited…

## The VIC-IV Screen Layout — https://retrocogs.mega65.com/2022/09/20/the-vic-iv-screen-layout/

With the addition of the VIC-IV, the Mega65 is not limited to a fixed sized screen anymore, the application can set the screen to any size up to 720 x 576 on PAL and 720 x 480 on NTSC.

The display is made up of two components, the border around the edges (light blue) and the characters that make up the screen (dark blue).

![Image 1](https://retrocogs.mega65.com/wp-content/uploads/2022/09/VIC4Screen1-1024x642.jpeg)

Laying out the screen really just comes down to figuring out how many visible characters you want (depends on the H&V scaling modes) and then calculating how much border is needed. Because I like to keep the screen centered I use the horizontal and vertical center values to base all of my calculations off of.

You can find the accompanying code here, [https://github.com/RetroCogs/Mega65Tutorials](https://github.com/RetroCogs/Mega65Tutorials), this tutorial is covered in _tutorial\_1\_screens.asm_.

## **Related Hardware Registers**

Here are the main registers that affect the layout of the screen :-

![Image 2](https://retrocogs.mega65.com/wp-content/uploads/2022/09/VIC4Screen_3-2.jpeg)
It is worth noting that while the majority of these registers are represented in ‘native’ pixels the VIC-IV adds two scaling modes for characters vertically and horizontally and depending on which scale you are using you may need to multiply some values by 2 (more details below).

## **CHRCOUNT, DISPROWS and LINESTEP**

The screen is made up with characters and in normal character mode each character takes up one byte, this means for an 80 column mode each line takes up 80 bytes. Once you know the size of your screen (either by deciding the number of columns and rows or by calculating it from the desired number of pixels wide and high) you will need to set the following.

**CHRCOUNT**= The number of characters in a row that you want the VIC-IV to draw, _note that there is currently a bug in the VHDL that makes values for CHRCOUNT > 255 not valid, once that bug is fixed I will remove this comment._

**DISPROWS** = The number of rows the VIC-IV should draw.

The VIC-IV can also specify how many bytes to step when moving to draw the next row, this is super handy when you want to define a screen area that is larger than the set of characters you are displaying, you will see this used in the next tutorial when we scroll the screen.

**LINESTEP**= The number of bytes to advance when moving to the next row.

![Image 3](https://retrocogs.mega65.com/wp-content/uploads/2022/09/VIC4Screen_2-2.jpeg)
## **Horizontal scaling modes : H640 vs H320**

When the Mega65 initially boots it is in H640 mode giving the display 80 characters wide, if you want to use the equivalent of the 40 column mode, you can disable bit 7 of $D031 to enable H320 mode.

The biggest thing to watch out for is that the layout registers (TEXTXPOS, SDBDRWDLSB) are measured in H640 values, when in H320 mode each 8 pixel wide character will be 16 pixels in the hardware registers. This means that if you want to move the screen one H320 pixel to the left you’ll need to move it two pixels in the registers.

## **Horizontal positioning**

To place the screen horizontally we need to specify :-

**SDBDRWDLSB&MSB H640** = pixel location of where the left border ends, horizontally the border is symmetrical and covers the same amount of screen left and right and so the value in $D05C,D is the number of pixels (both left and right in H640 units) that need to be covered.

**TEXTXPOS H640**= pixel location of where the left edge of the screen is located once again in H640 units.

First you’ll need to figure out how many visible pixels wide your screen is, to do this you can either take the number of characters wide and multiply by 8 or choose something appropriate for your selected H mode.

If you are in H320 mode, multiple by 2, this is the full width in H640 units of the visible screen.

_PixelsWide H640 = (NumCharacters * 8) * (H320 ? 2 : 1)_

As we’ve show above the horizontal center of the screen is at 400 and so the left edge of the screen will be located at :-

_LeftEdge H640 = 400 – (\_PixelsWide H640\_/ 2)_

Now that you have LeftEdge H640 you can set the hardware registers :-

**TEXTXPOS H640**= _LeftEdge H640_

**SDBDRWDLSB&MSB H640** = _LeftEdge H640_

Your screen will now be nicely centered.

## **Vertical scaling modes : V400 vs V200 modes**

When the Mega65 initially boots it’s in V200 mode giving the display 25 characters high, you can optionally choose 50 row mode by enabling bit 3 of $D031 to enable V400 mode._Be warned, V400 mode can get pretty hard to read on a CRT!!_

Note that all of the layout registers (TEXTYPOS, TBDRPOS, BBDRPOS) are measured in V400 values, so when in V200 mode each 8 pixel high character will be 16 pixels in the hardware registers. This means that if you want to move the screen one V200 pixel up you’ll need to move it two pixels in the registers.

## **Vertical positioning**

To place the screen vertically we need to specify :-

**TBDRPOS V400**= pixel location of where the top border ends.

**BBDRPOS V400**= pixel location of where the bottom border starts.

**TEXTYPOS V400**= pixel location of where the top edge of the screen is located once again in V400 units.

Figure out how many visible pixels high your screen is, to do this you can either take the number of characters high and multiply by 8 or choose a number that is appropriate for your selected V mode.

If you are in V200 mode, multiple by 2, this is the full height in V400 units of the visible screen.

_PixelsHigh V400 = (NumRows * 8) * (V200 ? 2 : 1)_

This is where is gets a little tricky, because PAL and NTSC have different number of lines the vertical center will depend on which video standard you are using, for now we will assume PAL and from the top diagram the vertical center of the screen is at 304 and so the top edge of the screen will therefore be located at :-

Top _Edge V400 = 304 – (\_PixelsHigh V400\_/ 2)_

Bot _Edge V400 = 304 + (PixelsHigh V400 / 2)_

Now that you have the TopEdge V400 and BotEdge V400 you can set the following registers.

**TEXTYPOS V400**= Top _Edge V400_

**TBDRPOS V400**= Top _Edge V400_

**BBDRPOS V400**= Bot _Edge V400_

And voila have a fully centered screen with the correct amount of border around it, you will end up with something like this, depending on your chosen H&V scale modes and size of screen.

![Image 4](https://retrocogs.mega65.com/wp-content/uploads/2022/09/VIC4Screen_4.jpeg)
In the next tutorial we will explain how to use a technique of shifting TEXTXPOS and TEXTYPOS to freely scroll the screen around in very few instructions.

Please free to leave comments and point out any mistakes, I want to keep these blog entries as a kind of living document that is always up to date and correct so future coders can use this as a reference site.

## VIC-IV graphics, using RRB for pixies — https://retrocogs.mega65.com/2025/08/14/vic-iv-graphics-using-rrb-for-pixies/

### Raster Rewrite Buffer

The Raster Rewrite Buffer is a new feature introduced in the Mega65, you can think of it as a 2048 pixel wide single line buffer. It allows a program to overlay extra characters on top of previously drawn chars which can be used for multiple layers of background or software sprites (pixies).

Within a screen row you can arbitrarily reset the horizontal drawing position by inserting a special character called a GOTOX char (bit 4 of color ram byte0).

Remember that with SEAM, each character is two bytes in screen RAM and color RAM. The following example we are drawing a GOTOX 0, followed by a number of NCM chars, a GOTOX 54 and then 1 NCM char for the sprite. You can see that we need this structure for every row of the screen.

```
SCREEN_DATA:
{
    .var choffs = (16384) / 64          // Character data at 16384
    .var choffs2 = (16384 + 64) / 64    // Character data at 16384 + 64

    // Repeat for every row of the screen
    //
    .for(var r = 0;r < LOGICAL_NUM_ROWS;r++) 
    {
        // GOTOX position
        .byte $00,$00

        // Row of characters
        //
        .for(var c = 0;c < CHARS_WIDE;c++) 
        {
            .var choffs = (16384) / 64    // Character data at 16384
            //Char index
            .byte <choffs,>choffs
        }

        // Draw a pixie
        //
        // GOTOX position
        .byte 54,0

        {
            // Char index
            .byte <choffs2,>choffs2
        }

        // End of line
        // GOTOX position
        .byte <320,(>320)&3

        // Char index 0
        .byte <0,>0
    }
}

COLOR_DATA:
{
    // Repeat for every row of the screen
    //
    .for(var r = 0;r < LOGICAL_NUM_ROWS;r++) 
    {
        // GOTOX marker - byte0bit4 = GOTOXMarker
        .byte $10,0

        // Row of characters
        //
        .for(var c = 0;c < CHARS_WIDE;c++) 
        {
            // Byte0bit3 = NCM
            // Byte1bit0-7 = Colour 255 index
            .byte $08,$ff
        }

        // Draw a pixie
        //
        // GOTOX marker - byte0bit7 = Transparent, byte0bit4 = GOTOXMarker
        .byte $90,$00

        // Byte0bit3 = NCM
        // Byte1bit0-7 = Colour 255 index
        .byte $08,$ff

        // End of line
        // GOTOX marker - byte0bit4 = GOTOXMarker
        .byte $10,$00

        // Byte1bit0-7 = Colour 255 index
        .byte $00,$ff
    }
}
```

The example would then show the following image.

![Image 1](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20240401165049-1024x133.png)
The RRB write position can be reset as many times as you need, when you’ve written all of your chars for the line you must remember to add an end of line (GOTOX screenWidth, char) pair to ensure the whole line is drawn.

You can also see in the above example that you want all of your back most layer to be opaque and then likely any overlay characters to be transparent (bit 7 of color ram byte 0).

### Character data layout

Both FCM and NCM characters are 64 bytes of data per character (8 bytes per line), you can think of memory as a huge vertical column of characters and so line 0 of char 2 is right after line 7 of char 1.

![Image 2](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20240401171557.png)
**NOTE** In screen data it refers to the character Index, you can calc this by (char mem / 64), so always take care to align your character memory to a 64 byte boundary.

### Handling Y Offsets

In order to be able to place pixies at arbitrary vertical positions we have to use the SEAM character data Y offset **fcm_yoffs** (screenRAM byte1: bits 5-7) feature of RRB, we also use **fcm_yoffs_dir** (screenRAM byte1: bit4), what this does is to subtract 8 bytes per value to the character data being fetched. When drawing, it shifts the character data being fetched down one line per value, a range of 0 to 7 pixels.

![Image 3](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20250814131301-1024x133.png)
You can see that for the top row the preceding character data is being shifted into view, to get around this we also need to use the rowmask feature **rowmask_flag** (colorRAM byte0:bit3) and the line mask is specified with **rowmask** (colorRAM byte1:bit0-7).

A **_true bit WILL write_** that line of character data

A **_false bit WILL NOT write_** that line.

So to put all of this together, when drawing a 16×8 pixie you will need to put chars into two rows, you will shift the character data down based on the pixie ypos and you will need to mask the top and bottom rows (red pixels below).

![Image 4](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20250814132750-1024x136.png)
In order to place a pixie vertically like the above picture you can use the following table to see which character indexes, y offsets and rowmasks you should use for the initial row and the following row.

|  | line 0 |  |  | line 1 |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| (ypos & 7) | chrPtr | -ve y offset | rowmask | chrPtr | -ve y offset | rowmask |
| 0 | chr | 0 | %111111111 | chr+1 | 0 | %00000000 |
| 1 | chr | 1 | %11111110 | chr+1 | 1 | %00000001 |
| 2 | chr | 2 | %11111100 | chr+1 | 2 | %00000011 |
| 3 | chr | 3 | %11111000 | chr+1 | 3 | %00000111 |
| 4 | chr | 4 | %11110000 | chr+1 | 4 | %00001111 |
| 5 | chr | 5 | %11100000 | chr+1 | 5 | %00011111 |
| 6 | chr | 6 | %11000000 | chr+1 | 6 | %00111111 |
| 7 | chr | 7 | %10000000 | chr+1 | 7 | %01111111 |

## VIC-IV graphics, setting up FCM and NCM — https://retrocogs.mega65.com/2025/08/13/vic-iv-graphics-setting-up-fcm-and-ncm/

**NOTE**_this doc is in progress and images will be added_

### Refresher on C64 background graphics

Due to the Mega65’s graphics being an extension of previous hardware, let’s have a little refresher on how background graphics works on the C64.

The VIC-II can only access 16KB and so we must select which bank of memory it’s data is residing in by modifying bits 0&1 of $dd00, this will select either (%11) $0000, (%10) $4000, (%01) $8000 or (%00) $c000. The screen and character ram locations are offsets within the selected bank.

The C64 screen is a fixed size of 40×25 characters (1000 bytes) and is split into screen RAM (offset from VIC-II bank using bits 4-7 of $d018) and color RAM (fixed location of $d800). Each element of the screen data is an index into a character set made up of 256 small images. Each of these characters take up 8 bytes so a total of 2048 bytes (offset from VIC-II bank using bits 0-3 of $d018).

The screen memory indicates which character graphics to display (8 bits) and the color memory indicates the color to use (lower 4 bits only).

With enough fancy footwork, you can achieve stunning screens like this BoozeDesign screen. [https://csdb.dk/release/?id=240696](https://csdb.dk/release/?id=240696)

![Image 1](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20250814234509-1024x650.png)

### Mega65 screen using SEAM (Super Extended Attribute Mode)

As we saw above, the VIC-II could reference 256 different characters per screen, the VIC-IV however can reference an impressive 8192 but clearly this can’t be done from a single byte.

In order to use the VIC-IV’s more advanced graphics modes we will use a feature called Super Extended Attribute Mode or SEAM for short, enabled with CHR16 (bit 0 of $d054)

```
// Enable Super Extended Attributes
        // Set bit0=16 bit char indices (SEAM)
        lda #%00000001
        tsb $d054
```

This expands all screen and color data to be 2 bytes per tile but in doing this it adds the following features.

*   Reference a character anywhere in the bottom 512KB (at a 64 byte granularity).
*   Per character we can select between Full color (FCM), Nibble color (NCM) and Mono.
*   Use the special GOTOX flag to jump the write position in the Raster Rewrite Buffer allowing for fancy multi-layered effects.
*   Vertical and Horizontal flipping of characters.
*   Right hand trimming of character pixels.
*   NCM palette selection per characters (choosing 1 of the available 16 color palettes).
*   Vertical shifting when the character data is read from RAM (I’ll go into all of the uses of this later).
*   Row masking allow you to select which rows of the character are drawn to the screen.
*   Foreground / Background priority compared to sprites.
*   Opaque / Transparent specifies if color index 0 writes to the screen or not allowing characters to be overlayed on top of each other.

When SEAM is enabled, remember that LINECOUNT ($d058,9) must now take into account that each character is 2 bytes so it’s typically set as LINECOUNT = CHRCOUNT * 2.

_Following images from mega65-chipset-reference.pdf_

![Image 2](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20250814224823.png)

![Image 3](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20250814224858.png)

### Palettes

The VIC-IV has 4 palettes of 256 colors each, to enable editing of the palettes you must first enable the PAL flag (bit 2 of $d030).

```
// Enable RAM palettes
        // Set bit2=PAL
        lda #%00000100
        tsb $d030
```

In order to access a palette for reading/writing you must select which is currently mapped by setting MAPEDPAL (bit 6&7 of $d070). Once a palette is selected you can read / write the Red bytes from $d100-d1ff, Green bytes from $d200-d2ff and Blue bytes from $d300-d3ff.

**NOTE** that for each value in palette RAM, the nibbles are flipped and so you must swap the lo and hi nibble to get a true 0 – 255 value. For example, a color of $37 should be stored as $73.

**NOTE** even though it looks like there should be 24 bits of colors displayable, the bottom bit of Red (bit 0) is reserved for genlock (not yet implemented) and so we can only display 2^23 colors (about 8 million).

You must lastly select which of the 4 palettes are to be used for Text, Alternate Text and Sprites. You do this by writing you selection to Text (BTPALSEL bit 4&5 $d070), Sprites (SPRPALSEL bit 2&3 $d070) and AlternateText (ABTPALSEL bit 0&1 $d070).

```
// Example Palette selection and choosing which to edit.
        // this chooses to edit pal 0, text and sprite are pal 0 and alt is pal 2
        //
        // MAPEDPAL, BTPALSEL,   SPRPALSEL,    ABTPALSEL
        // Edit=%00, Text = %00, Sprite = %00, Alt = %10
        lda #%00000010
        sta $d070
```

### Enabling FCM / NCM

In order to use either FCM or NCM we must first enable 8 bit color, this is done by clearing ATTR (bit 5 of $d031). We also want to enable FCM chars > 255, this means that any character index < 256 will show as Mono and any above 255 will show as FCM/NCM, this is enabled with FCLRHI (bit 2 of $d054).

```
// Disable VIC3 ATTR register to enable 8bit color
        // Clear bit5=ATTR
        lda #%00100000
        trb $d031

        // Enable Mono chars < $ff
        // Set bit2=FCM for chars >$ff
        lda #%00000100
        tsb $d054
```

### Full Color Mode (FCM)

FCM characters are 8 x 8 pixels and 256 colors per character.

![Image 4](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20250814230254.png)

When characters are rendering in FCM they use the full 256 colors per pixel which means the character data will use a byte per pixel, each byte selecting a color in the selected palette. FCM characters will consume 64 bytes of memory each and must be on a 64 byte alignment.

In FCM mode, color index 255 is handled specially, index 255 will not select the last palette color, instead it will select the color index specified by what’s in color RAM (byte1).

### Nibble Color Mode (NCM)

NCM characters are 16 x 8 pixels and 16 colors per character.

![Image 5](https://retrocogs.mega65.com/wp-content/uploads/2025/08/Pasted-image-20250814225543.png)

When characters are rendering in NCM they use 16 colors per pixel and each byte of character data represents 2 pixels, the left in the high nibble and the right in the low nibble. Each nibble is an index into a sub-palette that is selected with color RAM.

NCM characters also consume 64 bytes of memory each and must be on a 64 byte alignment.

In NCM mode, color index 15 is handled specially, index 15 will not select the last palette color, instead it will select the color index specified by what’s in color RAM (byte1 lo nibble). The sub-palette is selected using the value in color RAM (byte 1 hi nibble) so a color RAM value of $4f specifies that palette 4 is selected and color index 15 will use sub-palette color index 15.

## Scrolling the VIC-IV Screen — https://retrocogs.mega65.com/2022/10/04/scrolling-the-vic-iv-screen/

Unless all the action on your game is going to take place on a single screen you are going to want to scroll the screen. Using the VIC-IV there are a few methods of achieving this and in this tutorial we will show how to scroll the screen in all directions using the simplest method, by setting the screen and color buffers to a size larger than the screen and then modifying TextXPos, TextYPos, the screen pointer and color pointer.

The sample code is located here [https://github.com/RetroCogs/Mega65Tutorials](https://github.com/RetroCogs/Mega65Tutorials) and you will want to look at the source file **tutorial_2_scrolling.asm**

The video below shows what the sample will look like once compiled and run on either the Xemu emulator or when executed on real hardware (Mega65 or Nexys).

[Video 3](https://www.youtube.com/watch?v=5B7Pnj_YAQI)

## How the screen is sized and placed in memory

As a quick recap from the last tutorial we defined the following registers that specify with width, height and layout of the screen and color RAM :-

**CHRCOUNT** = The number of characters in a line that the VIC-IV will draw.

**DISPROWS** = Number of rows that the VIC-IV will draw.

**LINESTEP** = The number of bytes to advance when moving to the next row.

You will see in the diagram below that we’ve also introduced the following :-

**SCRNPTR** = The screen RAM pointer can be placed anywhere in RAM using this 32 bit pointer with byte granularity, for example, if you want to scroll the screen one character to the left you just add one byte to the screen RAM pointer.

**COLPTR** = Color RAM is represented as an offset from the location $FF80000, it is only a 16 bit offset so at largest your color RAM buffer can be up to 64k.

![Image 1](https://retrocogs.mega65.com/wp-content/uploads/2022/10/VIC4Scrolling1-1-1024x655.jpg)

Tip: _A general tip I use for all of my buffers is that I ensure that any buffer never crosses a 64k boundary, the benefit if we follow this is that once the upper 16 bits of a 32 bit address are set we never need to modify them and so moving a pointer to the next line for example is always just a 16 bit add. Here is how you set the 32 bit pointer in kick assember._

![Image 2](https://retrocogs.mega65.com/wp-content/uploads/2022/10/image-1.png)
But when updating the screen pointer you really only need to update $D060 and $d061 like this …

![Image 3](https://retrocogs.mega65.com/wp-content/uploads/2022/10/image-2.png)
## **Related Hardware Registers**

Here are the main registers that affect the layout of the screen, note the new additions for the tutorial in green :-

![Image 4](https://retrocogs.mega65.com/wp-content/uploads/2022/10/VIC4Scrolling2-3-1024x886.jpg)

## Horizontal scrolling

In order to scroll horizontally, first, we are going to set LINESTEP to be a value greater than CHRCOUNT, as an example, two 80 column screens wide would be a LINESTEP of 160 bytes.

In the sample we are using the value XPos to hold the horizontal scroll position, every frame we are taking this value subtracting it from the LEFT_BORDER H640 to create a new value for TEXTXPOS H640.

You can see in the diagram below that as XPos increases TEXTXPOS moves more and more to the left, this continues until a whole character has been scrolled at which point TEXTXPOS resets to LEFT_BORDER position and we increment the screen and color RAM pointers.

![Image 5](https://retrocogs.mega65.com/wp-content/uploads/2022/10/VIC4Scrolling3-4-1024x808.jpg)

* indicates to multiply by 2 if in H320 mode

You can also see that as we shift the screen to the left a space is appearing on the right, to remedy this we need to increment CHRCOUNT by one so in our example we will get the VIC-IV to draw 81 characters, the 80 that fit within the borders and one extra that shows up as we scroll.

We calculate the amount that we shift left from XPos, remember that if you are in H320 mode you will need to multiply by 2.

HShiftOffset H640 _= (XPos & 7) * (H320 ? 2 : 1)_

Now we can get the new TEXTXPOS by subtracting the HShiftOffset from LEFT_BORDER.

**TEXTXPOS H640** = LEFT_BORDER H640 – HShiftOffset H640

Screen and Color RAM offsets (the lower 16 bits) are calculated using the following.

**SCRNPTR(lohi)** = XPos / 8

**COLPTR(lohi)** = XPos / 8

In the sample program we are updating TEXTXPOS and the screen and color pointers every frame, this is only taking about 1/8 raster lines and is very fast to do.

## Vertical scrolling

Scrolling vertically is very similar to horizontal except that we shift the screen up by subtracting YPos from TOP_BORDER V400 and putting this into TEXTYPOS V400, when we’ve scrolled a full character we need to add LINECOUNT to the screen and color pointers.

Tip: _It is worth noting that if you are scrolling vertically you really want to choose a value that is easy to calculate, for example, a power of two (64, 128 etc) are just a number of shifts, or a combination of some shifts and some adds (160 = (Yc << 7) + (Yc << 5)). In the sample we create a table of row offsets which is fine if you are only scrolling by a screen or so but if your vertical height is large this would be a waste of memory and you will want to multiply to find the y component when calculating the screen and color RAM pointers._

We calculate the amount that we shift up from YPos, remember that if you are in V200 mode you will need to multiply by 2.

VShiftOffset V400 _= (YPos & 7) * (V200 ? 2 : 1)_

Now we can get the new TEXTYPOS by subtracting the VShiftOffset from TOP_BORDER.

**TEXTYPOS V400** = TOP_BORDER V400 – VShiftOffset V400

Screen and Color RAM offsets (the lower 16 bits) are calculated using the following.

**SCRNPTR(lohi)** = (XPos / 8) + ((YPos / 8) * LINESTEP)

**COLPTR(lohi)** = (XPos / 8) + ((YPos / 8) * LINESTEP)

You can see here we are adding both the horizontal and vertical character offsets to screen and color pointers in one equation.

As we scroll the screen vertically in this manner you will see a space showing up at the bottom of the screen, similar to how we solved the horizontal issue we need to add one to DISPROWS to get the VIC-IV to show one more row.

## Vertical limitations

Because we are calculating a new TEXTYPOS when scrolling vertically, we have to be sure that the new position is always >=0, because of this we need to limit the number of vertical lines you can scroll. I’ve added error validation into the sample to catch if you are trying to set the screen too tall.

![Image 6](https://retrocogs.mega65.com/wp-content/uploads/2022/10/image-1024x179.png)
## Conclusion

You will need to extend this technique to suit the specifics of your own game, especially around buffer sizes and LINESTEP values.

The next tutorial will be a short one and I’ll cover how to automatically handle NTSC vs PAL as until now we have been hardcoding our program to only handle one or the other.

Please free to leave comments and point out any mistakes, I want to keep these blog entries as a kind of living document that is always up to date and correct so future coders can use this as a reference site.
