# raw/assets/ — MEGA65 PDF library

Official PDF books downloaded from the [Documentation Landing Page](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21331992/Documentation+-+Landing+Page) via the Filehost (builds of **08 Apr 2026**, version 1.2 — Jenkins rebuilds these from `MEGA65/mega65-user-guide`, so re-download to refresh).

| File | Pages | Size | What it covers |
|---|---|---|---|
| mega65-userguide.pdf | 342 | 6.7M | Intro to the MEGA65 + condensed BASIC 65 command reference |
| mega65-basic65-reference.pdf | 345 | 4.6M | Every BASIC 65 command, function, operator |
| mega65-developer-guide.pdf | 351 | 68M | Writing programs for the MEGA65 (asm, C, BASIC; toolchains) |
| mega65-chipset-reference.pdf | 245 | 5.0M | Custom chips: 45GS02 CPU, VIC-IV, 45E100 Ethernet, registers |
| mega65-book.pdf | 1455 | 74M | The Complete Compendium — all volumes in one searchable PDF |
| MEGA65_BASIC_65_Referenzhandbuch_DE.pdf | 334 | 2.6M | German-language BASIC 65 reference (Günther Reiter, 65site.de) |

## Reading tips for agents

- The Read tool handles PDF page ranges (max 20 pages per request) — locate the topic first, then read the exact pages.
- **Prefer grepping the LaTeX source** in `raw/github/MEGA65-mega65-user-guide/` to locate content (same material, plain text), then open the PDF only when typeset tables/figures matter.
- The Compendium duplicates the other four books — search it when you don't know which volume covers a topic.

## Refresh

Latest hashed download URLs change per build. To re-fetch, query the Filehost catalog:
`curl -s "https://files.mega65.org/php/readversionlistpublic.php" | grep -o '{[^}]*"filename":"<name>.pdf"[^}]*}' | grep '"active":"Y"'`
and download `https://files.mega65.org/<location without ../>`.
