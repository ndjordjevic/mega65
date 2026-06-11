## Cross Development for Fun and Profit — https://dansanderson.com/mega65/cross-development/


Markdown Content:
Cross Development for Fun and Profit, part 1. [Dan’s MEGA65 Digest](https://dansanderson.com/mega65/) for June 2023.

[Audio 3](https://dansanderson.com/mega65/cross-development/M65Digest_2023June.mp3)

Cross Development for Fun and Profit, part 1.

[![Image 1: A program being written for the MEGA65, in Visual Studio Code on a Mac, in the XC=BASIC language](https://dansanderson.com/mega65/cross-development/tempconv.png)](https://dansanderson.com/mega65/cross-development/tempconv.png)

A program being written for the MEGA65, in Visual Studio Code on a Mac.

There’s something wholesome about writing a program on a vintage computer. Such a computer was designed to give equal attention to programs written by their operator and programs written by software companies, and included everything you would need to get started writing such programs. Compared to modern software development, the constraints of on-device retro coding can be comforting and inspiring. When all you have is a Commodore, some graph paper, and a reference manual, you can concentrate on creating programs and solving problems without distraction.

Professional software companies didn’t always do it this way. Larger companies often used other computers to produce Commodore software, such as a mainframe computer with larger storage, computation, and multi-user collaboration capabilities. They would write code using languages like C, and use specialized tools that combined the efforts of programmers and artists into data that could be written to a disk and run on a Commodore. Known as _cross development_, this workflow gave these companies a competitive advantage: they could work faster, collaborate better, reuse code across projects, and even develop their programs for multiple kinds of computers at the same time.

Today, many hobbyists use modern computers to write programs for vintage machines. There are so many good cross-development tools at our disposal that we can’t cover them all in one Digest. This month, we’ll consider the advantages of cross development, and survey a few tools you can use to write MEGA65 programs in BASIC and assembly language. We’ll highlight recent developments in these tools made specifically for MEGA65 programming. And we’ll introduce an exciting new cross-development language that has just added MEGA65 support: XC=BASIC.

## Featured Files

Three quick entertainments in this month’s selections.

[![Image 2: Bump Pocket, by MightyAxle](https://dansanderson.com/mega65/cross-development/bumppocket.png)](https://dansanderson.com/mega65/cross-development/bumppocket.png)

Bump Pocket, by MightyAxle.

[Bump Pocket](https://files.mega65.org/?id=7cbdae17-2d36-4599-bb44-b48b8aba4b7d), by MightyAxle. Collect colored orbs for points and dodge bombs in this action game, written in BASIC using CBM prg Studio. Use a joystick in port 2.

[![Image 3: 10 PRINT Racer 80 Column, by JaixBly](https://dansanderson.com/mega65/cross-development/10printracer.png)](https://dansanderson.com/mega65/cross-development/10printracer.png)

10 PRINT Racer 80 Column, by JaixBly.

[10 PRINT Racer 80 Column](https://files.mega65.org/?id=bd94ff20-af0a-4bb4-8829-6108679da41e) by JaixBly. Speed down a path cut through the famous [10 PRINT](https://10print.org/) pattern, in this conversion of [a game by Robin of 8-Bit Show and Tell](https://www.youtube.com/watch?v=bCTrdVhjjWo). Press 4 and 6 to move left and right.

[![Image 4: MegaPoly, by MirageBD](https://dansanderson.com/mega65/cross-development/megapoly.jpg)](https://dansanderson.com/mega65/cross-development/megapoly.jpg)

MegaPoly, by MirageBD.

[MegaPoly](https://files.mega65.org/?id=3c4067cf-2d89-46ca-a936-536b835e724e), by MirageBD. An homage to the [Amiga Boing Ball](http://www.generationamiga.com/2020/04/14/amiga-history-the-story-of-the-boing-ball/) demo, this modern take renders a smoothly animated rotating 3D shape using the MEGA65’s DMA hardware. Keep this running in the background at your next club meeting!

[![Image 5: MEGAVision project share logo](https://dansanderson.com/mega65/cross-development/megavision.png)](https://dansanderson.com/mega65/cross-development/megavision.png)

MEGAVision logo.

Mark your calendars! On Saturday July 1st at 7pm UTC (that’s 12 noon Pacific Time), Gurce is hosting the first ever _MEGAVision_, an online project share event hosted over [Zoom](https://zoom.us/). All topics are welcome, from hardware to software, completed projects or works in progress, or even just personal experiments that you don’t intend to upload to [Filehost](http://files.mega65.org/). And if you can’t make the date, you’re invited to pre-record a presentation to be shown at the event.

Contact Gurce [on Discord](http://mega65.org/chat) if you’d like to present something, and keep an eye out on Discord for further instructions. The meeting link will be made available just before the event.

## PaCommEx Northwest, Seattle, Washington, USA, June 24-25

[![Image 6: Pacific Commodore Expo Northwest 2023 banner](https://dansanderson.com/mega65/cross-development/pacommex_banner.png)](https://dansanderson.com/mega65/cross-development/pacommex_banner.png)

Pacific Commodore Expo Northwest 2023.

If you’ll be near the Pacific Northwest of the United States the weekend of June 24th through 25th, mark your calendars again! [Pacific Commodore Expo Northwest 2023](https://portcommodore.com/dokuwiki/doku.php?id=pacommex:start) is an annual gathering of Commodore enthusiasts in Seattle, Washington, hosted by Robert Bernardo, the Fresno Commodore User Group, and the Seattle Commodore Computer Club. This year’s venue is the Old Rainier Brewery Intraspace. Attendance is free, no tickets required!

I’ll be at PaCommEx all weekend giving talks and demos of the MEGA65. Challenge me with your toughest questions! If I don’t know the answer, I’ll make something up!

## Four-player joystick adapter

[![Image 7: The four-player joystick adapter for the MEGA65, produced by jim_64](https://dansanderson.com/mega65/cross-development/fourplayer.jpeg)](https://dansanderson.com/mega65/cross-development/fourplayer.jpeg)

The four-player joystick adapter for the MEGA65, produced by jim_64.

Like other Commodores, the MEGA65 includes two peripheral ports for joysticks and other controllers. That’s fine if you only have one friend, but what if you have more than one friend?

Paul Gardner-Stephens designed [a joystick port expansion interface](https://c65gs.blogspot.com/2018/12/super-simple-protovision-compatible.html) that connects to the expansion (cartridge) port of a MEGA65. Gurce [reproduced these results](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/7012353/Super+simple+Protovision-compatible+Joystick+Expander+for+MEGA65), and if you’re electronics savvy you can make your own.

Thanks to Jim of BIT Zeal (`jim_64` on the Discord), you can now [buy a pre-assembled four-player joystick interface](https://www.bit-zeal.com/product/4PlayerMEGA65/6) for the MEGA65. Jim has also put together “[Four Fun](https://files.mega65.org/html/main.php?id=4b46aca8-ec3b-4483-ae64-df1dfec3ee66),” a disk of four-player games that work with the adapter. Jim even includes a disk label for “Four Fun” when you buy the interface.

[![Image 8: Four Fun, a disk of four-player games for the MEGA65, compiled by jim_64](https://dansanderson.com/mega65/cross-development/fourfun.png)](https://dansanderson.com/mega65/cross-development/fourfun.png)

Four Fun, a disk of four-player games for the MEGA65, compiled by jim_64.

The MEGA65 four-player interface is inspired by a similar Commodore 64 peripheral that connected to the User port. Protovision makes [a modern version](https://www.protovision.games/hardw/4_player.php?language=en) of this peripheral, but it doesn’t work with the MEGA65 because the MEGA65 does not (yet) have a User port. However, both adapters use [the same software interface](https://www.protovision.games/hardw/build4player.php?language=en#codeit), so they should be compatible with the same four-player games.

See also Jim’s [Filehost page for the adapter](https://files.mega65.org/html/main.php?pr=b908ebb9-1145-4761-bd99-031f802d2a2f) for links to all of these resources.

## The cross-development workflow

Cross development tools allow you to use a modern computer to develop software for the MEGA65. Typically, you write your code as one or more text files using a modern programmer’s text editor such as [Visual Studio Code](https://code.visualstudio.com/). You use a tool called a _cross compiler_ to convert your text files into a program that your MEGA65 can run. In cross development terminology, the MEGA65 is the _target_ platform, and the computer you use to develop the software is the _host_ platform.

Typically, the output of a cross compiler targeting Commodore computers is a PRG file. You can put the PRG file on a D81 disk image using a program such as [droiD64](https://droid64.sourceforge.net/), which we looked at in [a previous issue of the Digest](https://dansanderson.com/mega65/back-to-basics/). Copy the D81 disk image to your MEGA65, then use the `DLOAD` and `RUN` commands at the `READY.` prompt to run the program.

It’s possible for a large program to consist of multiple files on one or more disk images. These are typically built with cross development tools to manage all of the code and data, and to create the disk images in an automated workflow. This is an advanced technique and requires specialized code to read from the disks. For this Digest, we’ll focus on single-file programs.

## Running your program

Having a quick and easy way to run code immediately after it is written is essential to the task of programming. This is easy enough if you’re running the software on the same computer where you wrote it: when you want to try your BASIC program, you simply type `RUN`. For cross development, that last step of getting the PRG to your MEGA65 can be a challenge. Moving the SD card back and forth between your PC and the MEGA65 for each bug fix would drive you crazy. Thankfully, there are other options.

### Running a PRG with Xemu

The most common way people cross develop for the MEGA65 is with the [Xemu emulator](https://github.lgb.hu/xemu/), which runs on your PC. Xemu is like having a MEGA65 on your computer, so you don’t have to transfer your program to another computer to test it. You’ll need a copy of [the latest ROM file](https://files.mega65.org/?ar=145591dd-deb6-4bd0-aa89-8e39cd021470), and you’ll follow [the Xemu MEGA65 Quick Start Guide](https://github.com/lgblgblgb/xemu/wiki/MEGA65-quickstart) to set it up.

An easy way to run a MEGA65 PRG file is to drag it into the running Xemu window, then click “Run/inject as PRG” in the dialog window that opens. A faster and nerdier way to run a PRG in Xemu is to start Xemu from the command line, using the `-prg` command line flag:

```
/Applications/Xemu/bin/xmega65 -prg hello.prg
```

I like to automate everything as much as possible, so I make this command part of a build script or shell command sequence so I can build and run my program in a single step. You can also put this along with your build command (such as `petcat`) in a [Visual Studio Code](https://code.visualstudio.com/) run configuration.

### Running a PRG on MEGA65 hardware

I also like to test my programs on an actual MEGA65 as much as possible. I use a device called a “JTAG adapter” that connects to the MEGA65 mainboard on one end and to my PC via a USB cable on the other. With this connected, I can use a PC app like M65Connect or the `m65` command line tool to beam a PRG file directly to the MEGA65. Search for “M65Connect” or “MEGA65 Tools” on [Filehost](https://files.mega65.org/) and download these tools for your PC’s operating system. If you want to go this route, see [detailed instructions in my MEGA65 Welcome Guide](https://dansanderson.com/mega65/welcome/using-jtag.html).

We won’t need the JTAG/UART method for much longer. The MEGA65 team has nearly completed a new feature that allows you to transfer files and run programs over the MEGA65’s ethernet jack connected to your local network. This hotly anticipated feature will enable much faster file transfers than a USB serial connection, and won’t require any additional hardware other than a common ethernet cable. Expect ethernet file transfer support later this year.

## Cross developing BASIC programs

In [a previous issue of the Digest](https://dansanderson.com/mega65/back-to-basics/), we introduced two tools for doing cross development of BASIC programs for the MEGA65. One of these is `petcat`, a command-line tool that takes a text file of BASIC code and produces a PRG file.

Here’s the example we used in the previous issue, a BASIC program that calculates the Celsius value for a temperature in Fahrenheit:

```
100 print "enter a temperature in degrees fahrenheit:"
110 input f
120 c=(f-32)*5/9
130 print
140 print f;" degrees fahrenheit is ";c;" degrees celsius."
```

To convert this to a MEGA65 PRG file using petcat, use this shell command:

```
petcat -w65 -o tempconv.prg -- tempconv.bas
```

The command-line tool `petcat` is included with the [VICE suite of Commodore emulators](https://vice-emu.sourceforge.io/). In late February, the VICE project accepted an update that completes its support for BASIC 65. This update has not yet been included in an official release of VICE. For the convenience of the MEGA65 community, I built [the latest version of petcat](https://files.mega65.org/?id=9561505c-a36d-4d3e-b158-d52a718e818e) for each major platform, so you can just download it and use it. Enjoy!

Also remember that there’s [a MEGA65 wiki page on petcat](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/27492353/Using+petcat+for+cross-developing+BASIC+programs) that describes how to use it and its text-based syntax.

## CBM PRG Studio 4.1.0 update

[![Image 9: CBM PRG Studio 4.1, with the character editor](https://dansanderson.com/mega65/cross-development/cbmprgstudio.png)](https://dansanderson.com/mega65/cross-development/cbmprgstudio.png)

CBM PRG Studio 4.1, with the character editor

[CBM PRG Studio](https://www.ajordison.co.uk/download.html) is a suite of tools for writing programs for Commodore computers with a visual interface for Windows. As we mentioned in a previous Digest, CBM PRG Studio added support for the MEGA65 with its version 4 release. Arthur Jordison continues to add MEGA65 features, and has just released version 4.1.

This new version includes a tool for composing music that can output `PLAY` commands, as well as a way to export `CHARDEF` statements from the character glyph editor. Support for BASIC 65 has been improved, and the assembly language workflow uses [Kick Assembler](http://theweb.dk/KickAssembler/Main.html#frontpage) for MEGA65 projects.

CBM PRG Studio is an all-in-one cross development suite for Commodore computers, and it’s exciting to see it get more and more useful for MEGA65 programming. If you run Windows on your PC, give the new version a try.

## What’s in a PRG?

When you save a BASIC program to disk on the MEGA65 using the `DSAVE` command, it creates a file of type PRG (short for “program”). This file can be loaded back into memory from disk using the `DLOAD` command. With cross development, you use a tool on a modern computer to produce a PRG file that can be loaded into the memory of a MEGA65.

Consider this simple BASIC program:

```
10 PRINT "MEGA65 RULES"
```

Here are the bytes of a PRG file for that program, in hexadecimal:

```
01 20 16 20 0a 00 99 20
22 4d 45 47 41 36 35 20
52 55 4c 45 53 22 00 00
00
```

The PRG file format is very simple: it contains raw data to be written to the MEGA65’s memory, along with the starting address. The address comes first, in Little Endian format (smallest digits first). In the case of a BASIC 65 program, the BASIC program data starts at address $2001, so the first two bytes of a BASIC 65 PRG file are $01 and $20. All remaining bytes are program data stored at that location.

BASIC 65 interprets the data bytes like so:

| Loaded address | PRG bytes | BASIC |
| --- | --- | --- |
| `2001` | `16``20` | Address of next line: $2016 |
| `2003` | `0A``00` | Line number: `10` |
| `2005` | `99` | Keyword token: `PRINT` |
| `2006` | `20` | Space |
| `2007` | `22``4d``45``47``41``36``35``20``52``55``4c``45``53``22` | `"MEGA65 RULES"` |
| `2015` | `00` | End of line |
| `2016` | `00``00` | End of program |

The `DLOAD` command makes no effort to validate that the data is a BASIC program or that it starts at a particular address. It just reads the starting address, then loads the data into memory at that address. This means that a PRG file can contain anything intended to be stored in memory. This could be machine code, or data such as graphics and music. You can write a BASIC program that contains `DLOAD` commands to populate regions of memory from multiple PRG files. Notice that each region must begin in the first 64 kilobytes of memory (with an address between $0000 and $FFFF), because there are only 16 bits (two bytes) for the address in a PRG file.

A common technique for cross development of machine code programs is to produce a PRG file that starts with a short BASIC program followed by the machine code. The BASIC program uses the `SYS` command to invoke the machine code program at the expected memory location. This allows the user to load everything into memory with a single `DLOAD` command, then start the program with the `RUN` command.

## Cross developing assembly language

Cross development is my favorite way to [write assembly language programs for the MEGA65](https://dansanderson.com/lab-notes/mega65-game-of-life-in-assembly/). Assembly language programs can get very long—literally one line of text per instruction—and it can be a big advantage to use modern text editing and source management tools to develop the code. A _cross assembler_ can take 45GS02 assembly language code and produce a machine language PRG file. You can create reusable libraries of routines in files shared across multiple projects, and even write _macros_ that can generate code in useful patterns.

My cross-assembler of choice for MEGA65 coding is the [Acme](https://sourceforge.net/projects/acme-crossass/) assembler by Marco Baye. I like it because it is fast, featureful, and written in portable C that can be built for any modern platform. It has a traditional assembly language syntax that is easy to learn. Best of all, Acme has native support for the MEGA65 and 45GS02 instructions and mnemonics (such as “LDQ”).

Here is a short Acme assembler source file that generates a BASIC launcher and a two-line machine code program:

```
!cpu m65
!to "hello.prg", cbm

* = $2001

!8 $12,$20,$0a,$00,$fe,$02,$20,$30,$3a,$9e,$20
!pet "$2014"
!8 $00,$00,$00

    inc $d020
    rts
```

You can see that this listing includes more than just the assembly language instructions for the program. It also includes instructions that tell the assembler how to produce the PRG file that we desire. The lines beginning with an exclamation point (`!`) tell Acme to perform certain actions, such as:

*   `!cpu` : Run in MEGA65 mode, including support for 45GS02 instructions.
*   `!to` : Generate a file named `"hello.prg"` in Commodore PRG format.
*   `!8` and `!pet` : Add some raw bytes to the PRG file that represent this short BASIC program: `10 BANK 0:SYS $2014` This program invokes the machine language code that follows the BASIC program in memory.

The 45GS02 CPU is exclusive to the MEGA65. It is based on the [65CE02 CPU](https://en.wikipedia.org/wiki/CSG_65CE02), a successor to the [65C02 CPU](https://en.wikipedia.org/wiki/WDC_65C02) which itself is a descendant of the 6502/6510 CPU we know from earlier Commodores. This means you can use a cross assembler for the 6502 CPU to write MEGA65 software, though you won’t be able to access all of its capabilities. A cross assembler needs to support 65CE02 instructions to access some features, such as the Z and B registers.

The 45GS02’s extensions to the 65CE02 all take the form of combinations of 65CE02 instructions. For example, even though the 45GS02’s “LDQ” is not an instruction of the 65CE02, you can invoke the “LDQ” instruction in a 65CE02 cross assembler with the magic incantation `NEG NEG LDA ...`. See appendices G and H in [the Compendium](https://mega65.org/docs) for a complete description of how this works. It’s pretty neat. The Acme assembler knows about 45GS02 instructions like “LDQ” and will generate the appropriate incantations automatically.

Many MEGA65 developers enjoy [Kick Assembler](http://theweb.dk/KickAssembler/Main.html#frontpage). The main release only supports 6502 and 65C02 instructions and not 65CE02 instructions, though [this fork by Jesper Balman Gravgaard](https://gitlab.com/jespergravgaard/kickassembler65ce02) adds support all the way up to the 45GS02. Kick has a rich feature set for writing and generating structured assembly language code, and is well loved by serious Commodore developers. [Shallan’s MEGA65 macro toolkit](https://github.com/smnjameson/S65) is written for Kick, which is a strong endorsement. Kick Assembler is written in Java and requires a Java runtime. And don’t miss [Kick Assembler 8-Bit Retro Studio](https://marketplace.visualstudio.com/items?itemName=paulhocker.kick-assembler-vscode-ext), a powerful extension for Visual Studio Code.

Other fine 6502 cross assemblers include [dasm](https://dasm-assembler.github.io/), [Ophis](https://michaelcmartin.github.io/Ophis/), and [ca65](https://cc65.github.io/). Note that each assembler has its own syntax, so be sure to read their manuals to figure out how to do things like the BASIC start-up routine. The Acme listing above will only work with Acme.

## XC=BASIC

Want the simplicity of BASIC with the power and speed of machine code? [XC=BASIC](https://xc-basic.net/) by Csaba Fekete is a cross-compiled BASIC-like language for Commodore computers. Csaba has just released [XC=BASIC version 3.2.0-beta](https://github.com/neilsf/xc-basic3/releases/tag/v3.2.0-beta) with support for the MEGA65.

Here’s that temperature conversion program written for XC=BASIC:

```
dim f as float
dim c as float
dim fstr as string * 20

print "enter a temperature in degrees fahrenheit:"
input fstr

f=val(fstr)
c=(f-32)*5/9
print ""
print f;" degrees fahrenheit is ";c;" degrees celsius."
```

This example only highlights a couple of features of the language, but they’re worth noticing. For starters, there are no line numbers. XC=BASIC uses named labels and subroutines to indicate how control flows through the program. This program does not make use of labels or subroutines, so it just executes instructions top to bottom.

XC=BASIC variables must be declared before they are used, and the declaration must say what _type_ of value will be stored in the variable. This differs from BASIC 65 (and other Commodore BASICs) that use a symbol like the dollar sign (`$`) at the end of the name to indicate the value type. In this example, the variables `f` and `c` are declared as floating point decimal values. These can contain numbers like 75.4 or -273.15.

The variable `fstr` is declared as a string, with a maximum length of 20. Unlike Commodore BASIC, strings must have a pre-declared maximum length, so that the memory can be allocated in advance by the compiler. Deciding on a maximum length requires extra effort during programming, but it helps the XC=BASIC compiler produce a faster and more memory-efficient program. This program uses the `input` statement to accept user input into the reserved string memory, then uses the `val()` function to convert the string to a floating point for use in the calculation. Also notice that the variable name can be a comfortable length, and is not limited to two letters as in Commodore BASIC.

XC=BASIC is a powerful language with many useful features for structuring and organizing large programs. The XC=BASIC compiler produces a machine code program, so the program runs much faster than BASIC 65, especially with the MEGA65’s 40 MHz processor speed. You can even [mix BASIC and assembly language code](https://xc-basic.net/doku.php?id=v3:asm) in the same XC=BASIC program.

The XC=BASIC compiler relies on the [dasm](https://dasm-assembler.github.io/) assembler mentioned earlier to produce the final PRG. As you get deeper into cross development, you’ll notice that a complete workflow often involves multiple tools, sometimes in a _tool chain_ where the output of one tool is used as the input of another, until the final tool produces a PRG or D81 disk image. In this case, the XC=BASIC compiler generates assembly language code intended for dasm, and dasm produces the PRG. (XC=BASIC invokes the assembler automatically.)

I was able to get XC=BASIC running on my Mac with the following steps:

1.   [Download dasm](https://dasm-assembler.github.io/). Expand the archive to get the `dasm` command line tool.
2.   [Download XC=BASIC 3.2.0-beta](https://github.com/neilsf/xc-basic3/releases/tag/v3.2.0-beta), using the “Source code” link (either zip or tar.gz). This archive contains pre-built command line tools in the `bin/` subdirectory, so you do not need to build this from source code.
3.   On a Mac, you need to tell macOS that it’s okay to run these tools even though they lack Apple developer signatures. Use these commands: `xattr -d com.apple.quarantine dasm; xattr -d com.apple.quarantine xc-basic3-3.2.0-beta/bin/macOS/xcbasic3`
4.   The `dasm` command must be on the command path for your shell. For example, if the `dasm` tool is located at `/Users/yourname/Downloads/dasm`, this command adds the folder to the command path: `export PATH=$PATH:/Users/yourname/Downloads`

To compile a program for the MEGA65, invoke the `xcbasic3` command with the `--target=mega65` option.

```
xcbasic3 --target=mega65 tempconv.bas tempconv.prg
```

* * *

I’m as nostalgic for the days of writing programs directly on my Commodore as anyone else, and I still do it sometimes. I use cross development for larger projects for several reasons. On a modern machine, I can type faster, I can save and backup multiple versions of my code more easily, and I can use more powerful tools and languages to write programs. Eventually we’ll have more on-device programming tools like [Mega Assembler](https://files.mega65.org/?id=3b101d41-5128-4a21-879c-0cf7988edfec) so I can do more without leaving the comfort of the MEGA65. Both methods have their place.

In next month’s Digest, we’ll continue exploring cross development tools, with a look at programming your MEGA65 using the C language, as well as a language that’s newer than any of our vintage computers, called Rust.

Until then!

— Dan
