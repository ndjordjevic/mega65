# c64-wiki.com

## Fetch log
- Inbox URL: https://www.c64-wiki.com/wiki/mega65
- Final URL: https://www.c64-wiki.com/wiki/mega65
- Fetched: 2026-06-10
- Pages: 1
- Mode: brief
- Note: single encyclopedia article (flagged on-wiki as a stub; some specs dated, e.g. "compact devkit form planned for 2020").

## MEGA65 article — https://www.c64-wiki.com/wiki/mega65

From C64-Wiki

[Jump to navigation](https://www.c64-wiki.com/wiki/mega65#column-one)[Jump to search](https://www.c64-wiki.com/wiki/mega65#searchInput)

[![Image 1: Stub](https://www.c64-wiki.com/images/6/68/Schild_stub.png)](https://www.c64-wiki.com/wiki/File:Schild_stub.png "Stub")**This article is very short and not very detailed. Please help to improve it.**

MEGA65
[![Image 2: Mega65 Prototype](https://www.c64-wiki.com/images/thumb/3/33/Mega65Prototype.jpg/300px-Mega65Prototype.jpg)](https://www.c64-wiki.com/wiki/File:Mega65Prototype.jpg "Mega65 Prototype")
**Type:**[Home Computer](https://www.c64-wiki.com/wiki/Home_Computer "Home Computer")
**Producer:**[http://mega65.org/](http://mega65.org/) and the [Museum of Electronic Games & Art](http://m-e-g-a.org/)
**Price:**666.66€ (net)
**Released:**2021
**Discontinued:**—
**[Processor](https://www.c64-wiki.com/wiki/Processor "Processor"):**8-bit [GS4510](https://www.c64-wiki.com/index.php?title=GS4510&action=edit&redlink=1 "GS4510 (page does not exist)") at 40.5 MHz
**[Memory](https://www.c64-wiki.com/wiki/Memory "Memory"):**384 KB fast RAM, 8MB of "Hyper RAM" (aka. Attic RAM).
**[OS](https://www.c64-wiki.com/wiki/OS "OS"):***   [MEGA OS](https://www.c64-wiki.com/wiki/MEGA_OS "MEGA OS") hypervisor
*   [BASIC 10](https://www.c64-wiki.com/wiki/BASIC_10 "BASIC 10") or [BASIC 65](https://www.c64-wiki.com/wiki/BASIC_65 "BASIC 65")
*   [GEOS 64](https://www.c64-wiki.com/wiki/GEOS "GEOS")[[1]](https://www.c64-wiki.com/wiki/mega65#cite_note-1)
*   [Contiki](https://www.c64-wiki.com/wiki/Contiki "Contiki")
**Info:**Open source implementation of an enhanced [Commodore 65](https://www.c64-wiki.com/wiki/Commodore_65 "Commodore 65").

The **MEGA65** is a 100% open-source implementation of the official (but never-released) [Commodore 65](https://www.c64-wiki.com/wiki/Commodore_65 "Commodore 65") computer. It is in development by associates of the [Museum of Electronic Games and Art e. V.](https://www.c64-wiki.com/wiki/MEGA_-_Museum_of_Electronic_Games_and_Art "MEGA - Museum of Electronic Games and Art"), a not-for-profit institution "dedicated to the preservation of our digital heritage." As well as the original C65 design, the MEGA65 provides additional hardware and software enhancements, including a choice of using BASIC 10 or [BASIC 65](https://www.c64-wiki.com/wiki/BASIC_65 "BASIC 65") (containing improvements that go beyond [BASIC 10](https://www.c64-wiki.com/wiki/BASIC_10 "BASIC 10")), and the MAC-like graphical user interface, GEOS. This video shows GEOS running in hi-res (at about 1 min 10 sec): [https://www.youtube.com/watch?v=EvMjBCuuedk](https://www.youtube.com/watch?v=EvMjBCuuedk)

The MEGA65 has an 8-bit [CPU](https://www.c64-wiki.com/wiki/CPU "CPU") with additional 32-bit instructions implemented in [FPGA](https://www.c64-wiki.com/index.php?title=FPGA&action=edit&redlink=1 "FPGA (page does not exist)"). Like the original C65, it also has a Commodore 64 mode with a level of compatibility similar to that of the Commodore 128 running in C64 mode. It features HDMI and other modern improvements.

## Hardware Specifications[[edit](https://www.c64-wiki.com/index.php?title=MEGA65&veaction=edit&section=1 "Edit section: Hardware Specifications") | [edit source](https://www.c64-wiki.com/index.php?title=MEGA65&action=edit&section=1 "Edit section's source code: Hardware Specifications")]

*   **[CPU](https://www.c64-wiki.com/wiki/CPU "CPU")**: GS4510 single-core, switchable between 1, 2, 3.5 and 40.5MHz, in-order, no-branch-prediction, no-cache, single-scalar, no-fpu, no-smd, no-HCF, non-pipelined, enhanced 4502 8-bit processor, with 32-bit ZP indirect and 32-bit far-JSR/JMP/RTS operations, 28-bit address space, fast hypervisor traps, virtual memory, IO virtualisation (coming soon).
*   **Speed**: Synthmark64 score: 44.5x (C64 = 1x). Bouldermark score: 29,970 (C64 = 313).
*   **[DMA](https://www.c64-wiki.com/index.php?title=DMA&action=edit&redlink=1 "DMA (page does not exist)")**: C65 DMAgic compatible DMA controller. Fills at 40MB/sec, copies at 20MB/sec, swaps at 10MB/sec.
*   **[Video Controller](https://www.c64-wiki.com/index.php?title=Video_Controller&action=edit&redlink=1 "Video Controller (page does not exist)")**: VIC-IV advanced rasterised video controller, like the VIC-II and VIC-III no framebuffer. Native resolution 720x576 (81MHz internal and 27MHz output pixel clock). Supports all documented [VIC-II](https://www.c64-wiki.com/wiki/VIC-II "VIC-II") modes (hi-res, multi-colour mode, extended-background-colour mode, sprites) and VIC-III modes (bitplanes are in the process of adding). Independent horizontal and vertical hardware scaling allows text and graphics resolutions between the native resolution and as low as 60x38. Separate 256-colour palettes for sprites, bitplanes and character graphics, allowing upto 1,024 colours on screen without changing the palette in real-time. VGA output 12-bit (4,096 colours). The planned DVI/HDMI output will support 23-bit colour (8.3 million colours). Text mode extensions including proportional width characters, super-extended background colour mode, as well as the standard VIC-III extended attributes.
*   **[Sound](https://www.c64-wiki.com/index.php?title=Sound&action=edit&redlink=1 "Sound (page does not exist)")**: Quad soft-SIDs + dual 8-bit DACs.
*   **[RAM](https://www.c64-wiki.com/wiki/RAM "RAM")**: 384KB RAM visible to VIC-IV, 32KB colour RAM visible to VIC-IV. 8MB of Hyper RAM (aka Attic RAM).
*   **Media**: D81 disk images from SD card (native VFAT32 file system support coming soon). Real 3.5" floppy drive support. Standard loading speed without fast loader ~20KB second. Loading speed direct from SD card 300 - 3000KB/second (1200 - 12000 blocks per second), depending on SD card.
*   **Outputs**: VGA, 10/100mbit Ethernet, Stereo Audio (Stereo soon), JTAG/USB/serial debug interface, HDMI, Expansion Port, external disk drive interface compatible with c64 disk drives.
*   **Inputs**: Ethernet, Micro SD slot, real-time clock, joystick ports 1 and 2 (9-Pin Atari Standard).
*   **[Operating System](https://www.c64-wiki.com/wiki/Operating_System "Operating System")**: MEGA-OS all-in-one hypervisor and compat operating system, including integrated freezer and task switcher, VFAT32 file system driver and inter-process communications.
*   **Form factor**: C65-like all-in-one. Compact devkit form planned for 2020.
*   **Supported FGPAs**: Nexys4DDR (and variants), MEGA65 custom PCB, and TE0725 development board. These boards include a Xilinx Artix7 100T FPGA, which is a high-performance [FPGA](https://www.c64-wiki.com/index.php?title=FPGA&action=edit&redlink=1 "FPGA (page does not exist)"), much faster and larger than the Spartan FPGAs used in other retro computing projects. Unfortunately the old Spartan FPGA boards cannot run the MEGA65 core.

## Books[[edit](https://www.c64-wiki.com/index.php?title=MEGA65&veaction=edit&section=2 "Edit section: Books") | [edit source](https://www.c64-wiki.com/index.php?title=MEGA65&action=edit&section=2 "Edit section's source code: Books")]

There are five different MEGA65 user guides that contain information about different aspects of the MEGA65:[[2]](https://www.c64-wiki.com/wiki/mega65#cite_note-2)

*   [MEGA65 Book](https://www.c64-wiki.com/index.php?title=MEGA65_Book&action=edit&redlink=1 "MEGA65 Book (page does not exist)") (1069 pages)
*   [MEGA65 Developer Guide](https://www.c64-wiki.com/index.php?title=MEGA65_Developer_Guide&action=edit&redlink=1 "MEGA65 Developer Guide (page does not exist)") (267 pages)
*   [MEGA65 Userguide](https://www.c64-wiki.com/index.php?title=MEGA65_Userguide&action=edit&redlink=1 "MEGA65 Userguide (page does not exist)") (260 pages)
*   [MEGA65 BASIC 65 Reference](https://www.c64-wiki.com/index.php?title=MEGA65_BASIC_65_Reference&action=edit&redlink=1 "MEGA65 BASIC 65 Reference (page does not exist)") (285 pages)
*   [MEGA65 Chipset Reference](https://www.c64-wiki.com/index.php?title=MEGA65_Chipset_Reference&action=edit&redlink=1 "MEGA65 Chipset Reference (page does not exist)") (188 pages)

## References[[edit](https://www.c64-wiki.com/index.php?title=MEGA65&veaction=edit&section=3 "Edit section: References") | [edit source](https://www.c64-wiki.com/index.php?title=MEGA65&action=edit&section=3 "Edit section's source code: References")]

1.   [↑](https://www.c64-wiki.com/wiki/mega65#cite_ref-1)[http://c65gs.blogspot.de/2016/08/we-can-include-geos-with-mega65.html MEGA65-Blog](http://c65gs.blogspot.de/2016/08/we-can-include-geos-with-mega65.html)
2.   [↑](https://www.c64-wiki.com/wiki/mega65#cite_ref-2)[MEGA65 documentations](https://files.mega65.org/manuals-upload/)

## Links[[edit](https://www.c64-wiki.com/index.php?title=MEGA65&veaction=edit&section=4 "Edit section: Links") | [edit source](https://www.c64-wiki.com/index.php?title=MEGA65&action=edit&section=4 "Edit section's source code: Links")]
