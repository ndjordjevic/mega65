# Super Extended Attribute Mode

- URL: https://dansanderson.com/mega65/super-extended-attribute-mode/
- Published: October 1, 2025
- Fetched: 2026-06-11

## Overview

Explores Super Extended Attribute Mode (SEAM), which doubles memory allocation per character to 16 bits for both screen and color data — enabling 8,192 possible characters per character set (vs standard 256).

## Key Concepts

**Color Expansion**: The MEGA65 supports up to 8,388,608 colors via a two-part system: 16 "major" color levels (0–15) plus 16 fractional "minor" levels per component. Palette memory: 4 bits major + 4 bits minor per byte.

**Full-Palette Low-res Multicolor Mode**: Access all 256 palette entries within multicolor character mode using 8-bit color values instead of the standard 5-bit limitation.

**CHR16 Screen Codes**: SEAM expands screen codes from 8 bits (256 chars) to 13 bits (8,192 chars). Allows displaying uppercase, lowercase, and PETSCII graphics simultaneously.

**Bitmap Graphics Trick**: Fill the 2,000-character display with unique screen codes, then treat the character set itself as a bitmap — each character definition becomes individual pixels of a 640×200 display.

## Code Examples

Complete BASIC 65 programs demonstrating palette manipulation and complex bitmap drawing routines using bitwise operations are provided in the article.

## Note

This is the 40th issue and three-year anniversary of Dan's MEGA65 Digest.

## Related Projects Announced

- Mega-IP: TCP/IP networking stack for BASIC 65
- Super Mega Assembler: self-hosting assembler in machine code
- MegaPET: officially released Commodore PET core
- Mega65-AGI: enables playing King's Quest on MEGA65
