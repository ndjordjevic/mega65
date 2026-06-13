# MiSTer2MEGA65 Explained

## Metadata
- Video ID: 9Ib7z64z9N4
- Channel: Oliver Graf
- Duration: 18:52
- Upload date: 2022-03-21
- URL: https://www.youtube.com/watch?v=9Ib7z64z9N4
- Fetched: 2026-06-13

## Description
So what about alternate cores for the MEGA65? Well there is the MiSTer2MEGA65 framework and I am going to explain what it does.

The framework and the cores where created by Sy2002 and MJoergen.

MiSTer2MEGA65 Framework: https://github.com/sy2002/MiSTer2MEGA65
Alternate MEGA65 cores: https://sy2002.github.io/m65cores/
MiSTer Project: https://github.com/MiSTer-devel/Main_MiSTer/wiki

Comaland Demo by Oxyron: http://www.oxyron.de/
Doc Cosmos by Shallan50k: https://www.twitch.tv/shallan50k

## Chapters
| # | Title | Timestamp |
|---|---|---|
| 1 | Intro | 0:00 |
| 2 | What are we talking about? | 0:30 |
| 3 | FPGA Basics | 1:47 |
| 4 | MEGA65 Basics | 2:51 |
| 5 | MiSTer Basics | 4:07 |
| 6 | Differences | 5:36 |
| 7 | MiSTer2MEGA65 | 6:24 |
| 8 | Schematics | 7:28 |
| 9 | How to port a core | 8:48 |
| 10 | C64 core demo - Part 1 | 10:08 |
| 11 | C64 core demo - Part 2 | 15:39 |
| 12 | Outro | 18:26 |

## Transcript

### Intro (0:00)
Hello, I know it has been a long time since my last video but work did interfere with hobby — sorry. And yes, I did promise a Mandelbrot video about full color graphics mode, and as you can see from the title screen, that is not what I'm going to talk about today. Instead I will be talking about the MiSTer2MEGA65 framework. The goal is to explain what it is, and what it can do and what it won't do.

### What are we talking about? (0:30)
Obviously we are talking about the MEGA65, the new retro home computer system which hopefully will be in the hands of the first 400 people shortly. But the MEGA65 is also an FPGA core which enables the hardware to work as an enhanced C65 system with a bit of backward compatibility to the C64. But it is not completely compatible — for one it does have a more advanced CPU which will not work as the old 6502 did. But can we have a real C64, please? Or VIC-20? Or Amiga? Or some other vintage Commodore — or even non-Commodore — home computer on this nice hardware? Well, actually all those platforms have already been converted to FPGA cores for other projects. For example, the MiSTer project has a lot of them. So can we just load those cores on the MEGA65? It has an FPGA as the MiSTer does, right? Let me first take a step back before I answer this.

### FPGA Basics (1:47)
Because it might be best to first explain what the FPGA really is. In essence it is a chip that can be changed. Normally a chip is fixed in what it can do because all the circuits are hardwired in the silicon. The FPGA is different — it consists of many logical elements, flip-flops, and memory cells which can be connected and reconfigured by a programming bitstream. So the FPGA is not an emulation because it really reassembles the circuits and hardware. There is no modern processor inside that will try to act like a vintage processor — the circuits and elements on the FPGA will behave like a real circuit down to timing and electrical levels. That brings us to the next logical conclusion: you can't run an FPGA core in an emulator like Xemu, mainly because the whole emulation of electrical circuits is so complex that the computer can't really handle this in real time, even for a one-megahertz CPU.

### MEGA65 Basics (2:51)
Let's take a look at the MEGA65. It is a complete home computer system as you would have been able to buy in the good old days. It is in one case which has the keyboard and the floppy drive included and has various interfaces to the outside. Inside of it is a custom PCB with a Xilinx Artix-7 FPGA on it. It is the biggest of the series which has 215,000 logical elements and around 13 million bits of RAM. And this is all — there is no hard processing system inside. HPS is what we call a fixed CPU, that is, one you can't change, opposite to the FPGA which can be changed. The interfaces include VGA, HDMI, IEC for external devices, internal and external SD card slots, DB9 for joystick and mouse, a custom keyboard with PETSCII characters, a real 3.5-inch floppy drive, and a cartridge slot.

### MiSTer Basics (4:07)
The MiSTer on the other hand is no complete system in itself. It runs on the Terasic DE10-Nano board, which is a development board for educational use, and has an Intel Cyclone 5 SoC on it. This Cyclone 5 system-on-a-chip is not only an FPGA — it also has a dual-core ARM Cortex-A9 CPU on it. The FPGA itself has 110,000 logical elements and 5.5 million bits of RAM. On the interface side the DE10 board provides USB OTG interface, USB FTDI programming interface, SD card slot, HDMI, mono audio jack, some onboard peripherals, and an external connection header to add custom stuff. Most of the time you will also buy a USB data board, an analog I/O board, some extra fast RAM, perhaps a real-time clock — available in various configurations.

### Differences (5:36)
Well, back to the question: can we just run the MiSTer cores on the MEGA65? The short answer is no — sorry, you can't do that. But why? First, the MiSTer does not only use an FPGA — it also has this on-chip ARM CPU which runs Linux and is used for various functions, for example SD card access. It also has all those expansion boards and USB, but the MEGA65 has its own keyboard interface and various other ports that are not comparable to the MiSTer expansions. FPGA-wise, the MEGA65's Artix-7 chip has more resources than the Cyclone 5 FPGA — so that is a good point.

### MiSTer2MEGA65 (6:24)
I think the title of the video already gave it away — there is a way. This way is called MiSTer to MEGA65, which is a programming framework to develop MEGA65 cores or port already existing cores to the MEGA65 hardware. So it is not a MiSTer core player which you simply run on your MEGA65 to play MiSTer cores — this is not possible. It is a base that provides a hardware abstraction for the MEGA65 system by providing VHDL components that allow for easy interfacing. This includes keyboard, peripherals, HDMI output, audio processing, and RAM interface. It also includes a CPU which is called QNICE. This is the replacement for the ARM CPU of the MiSTer system and provides on-screen display and SD card access — for MEGA65 you could compare it to the Hypervisor and Freezer components.

### Schematics (7:28)
Let's try to visualize this. This does not aim to be a complete schematic of the two systems — it is only meant to show certain parts to understand how they differ. On the left you can see the MiSTer Cyclone 5 SoC with its FPGA part and the ARM CPU — certain external functions are provided through the CPU. The bitstream of the core is programmed into the FPGA, which also has direct external connections. On the right the Artix-7 FPGA of the MEGA65 is shown. In light orange: the MiSTer2MEGA65 framework, which is part of the bitstream that is programmed into the FPGA. The rest might be circuits for the MiSTer core that uses the M2M framework. The idea of the framework is that you should not need to change the MiSTer core — you only need to change the way the core is connected to the framework. That way future changes of the MiSTer core can easily be integrated into its MEGA65 port. This could actually result in improvements that could be ported back to the original MiSTer core.

### How to port a core (8:48)
Now you might say — where do I start? I want to port my favorite system. Good news: with two MiSTer cores already ported and the third in progress, the MiSTer2MEGA65 framework gets more and more well defined every day. But to really get going you should be able to redesign a circuit in hardware description language. It might seem like programming but there are certain constraints that you should know and keep in mind — so don't let yourself be discouraged, there are lots of resources and people out there that can jumpstart you. The documentation of the framework is currently a bit bare-bones but it will be updated soon so that all the various functions and interfaces are described. There are also the existing cores for reference. And who knows, perhaps I will port some easy core and make videos about it — tell me in the comments if this sounds interesting.

### C64 core demo - Part 1 (10:08)
So I did talk about two cores already available and the third one in development. If you follow us on Discord you already know that this is the C64 core, and it has nearly reached a state that could be defined as alpha — so let's take a look. First we need to switch on the MEGA65, which will then come up in MEGA65 mode. (Apologies for the shifter display — this is my really cheap VGA to HDMI converter.) Now I will put the C64 bitstream via m65 tool onto the MEGA65 and switch to the HDMI output of the C64 core, which can also do VGA output. Let's load some nice demo to get a look — I have to load the disk via serial console. Lot speed is standard for 1541, no JiffyDOS here. [Demo loading — Comaland demo by Oxyron plays on screen.] So we won't flip the disk — this is for discs long, it's the Comaland demo, so just download it and view it on your own system.

### C64 core demo - Part 2 (15:39)
I will now load a different bitstream just to show something else and insert a game, and then we will see a first preview of the on-screen display. While loading the game I can show you what happens if I press the Help button — a pop-up will appear. With this you will then be able to do things; currently not much works — only the Hz selection and triple buffering — but later you will be able to change the disk in the drive, or load a cartridge into the system, or change the SID mode and various other stuff, perhaps something like CRT emulation. [Game "Doc Cosmos" by Shallan50k loads and plays.] So as I said I'm not really good at playing — only dying. So let's conclude this short demo of the C64 core.

### Outro (18:26)
We have reached the end of this quick overview of the MiSTer2MEGA65 framework, created by MJoergen and Sy2002, who also created the three MiSTer core ports. If you still have questions, feel free to ask them in the comments or join the MEGA65 Discord where you will get more or less direct feedback depending on the time of day. Until next time — bye bye!
