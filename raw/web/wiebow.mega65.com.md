# wiebow.mega65.com

## Fetch log
- Inbox URL: https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/
- Final URL: https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/
- Fetched: 2026-06-10
- Pages: 1
- Mode: standard
- Note: single tutorial article capture (the inbox URL targets one post, treated as the page of interest on this blog).

## Cross development for the MEGA65 — https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/

## Introduction

![Image 1: mega65-cross-development.jpg](https://wiebow.mega65.com/wp-content/uploads/2023/12/image.jpeg)

**My setup, with a network cable between the PC and the MEGA65, showing HELLO WORLD running.**

This post is about setting up a development system to program in _Assembly_ on PC. The compiled program needs to be deployed to an emulator and to the MEGA65 itself.

_Cross Assembly_ is a method to write and assemble programs in assembly language other than the native CPU of the development machine. An example is programming and compiling 6502 code on a modern AMD or Intel CPU based PC. The program file is run on the target machine, or in an emulator on the development machine. An example is the[CBM prg Studio](https://www.c64-wiki.com/wiki/CBM_prg_Studio)suite of programs for Windows in combination with [VICE](https://vice-emu.sourceforge.io/).

We’ll need the following ingredients:

*   An assembler.
*   A text editor, preferably with syntax highlighting.
*   A build system to: 
    *   Assemble the program file.
    *   Create a disk image file containing the program file.

*   Deploy to: 
    *   An Emulator for quick iteration.
    *   The MEGA65 itself, using a physical connection.

*   A Debugger for when the inevitable happens.

> This post and setup is written using **Linux Mint** as the operating system. The file paths on a Windows or Apple computer will be different but the same principles apply.

## System setup

First, lets add all the necessary programs and tools to our system.

### File system

I place my development files in my home directory, in the folder `~/development/mega65`. This folder has a `tools` sub-folder for the necessary tools and a `project` folder for each … yes … project.

### Assembler

There is a choice in assemblers, and I use **Kick Assembler**. For full MEGA65 development a [modified version of Kick Assembler](https://gitlab.com/jespergravgaard/kickassembler65ce02/-/releases) is required which supports the 45GS02 instruction set.

Place the `KickAss65CE02-5.25.jar` file in `~/development/mega65/tools/kickass/`

Also ensure that **Java** is installed. This can be checked by entering `java --version` on the command-line.

### Disk Image

Kick Assembler itself can make a .D64 disk image file which cannot be mounted (yet) on the MEGA65. But, there is a tool called `c1541` that comes with the **VICE** emulator that can create .D81 disk images.

To get this file, I install the Linux version of **VICE** via the _Software Manager_, and copy the `c1541` executable from `/usr/bin` folder to the `tools` folder.

> **Kick Assembler** includes a java version of the same program, but I have not found how to make a .D81 disk image file instead of a .D64 image file. Please let me know if you have any tips. This would remove one more tool from the chain.

### Emulator

An emulator speeds up development as the program can be run locally, and there are various debugging tools available in the emulator to speed up trouble-shooting. For the MEGA65, the choice is **Xemu**. The GitHub repository for Xemu can be found [here](https://github.com/lgblgblgb/xemu), and a setup guide is provided on its [WIKI](https://github.com/lgblgblgb/xemu/wiki/MEGA65-quickstart).

To emulate the MEGA65, you need the `mega65.rom` file. For MEGA65 owners this file can be found on the FileHost in the member area, or on the internal SD card inside the MEGA65.

> Ideally, the ROM file should be the same as used on the physical MEGA65.

### Text editor

I use **Sublime Text**; I love the speed and versatility of this program. To make Sublime Text recognise the 45GS02 instructions a _language file_ is required. [I forked a repository](https://github.com/wiebow/M65_KickAsm_Macros) with a language file.

The language file `KickAssembler (Mega65).sublime-syntax` must be placed inside `~/.config/sublime-text/Packages/User`.

Inside Sublime Text a build system is made using **Tools > Build System > New Build System…** with the following content:

```
{
	"shell_cmd": "./make.sh"
}
```

I call this build system `Kickassembler (M65)`. This build system can be selected in Sublime Text via **Tools > Build System**, and after that, pressing `CTRL-B` will start the shell script.

### Physical Deployment

We deploy to an emulator and to the MEGA65 itself. An emulator, as fine as it is for quick iterations, has some drawbacks: not EVERYTHING is emulated correctly. So we also need to push the program file to the MEGA65 and run it locally.

You can connect the MEGA65 to your PC in two different ways:

*   **Serial**: via JTAG (serial over USB) connector
*   **Network**: via the network port, using a network cable between the PC and the MEGA65.

Both methods work, it’s up to you to decide which one to use. I use the network connection as this seems to be the way forward and it is already faster to use than the serial connection.

> I am using a network cable DIRECTLY from my PC to the MEGA65. All my other networking is done through another network interface. Using Link-Local IPv6 configuration works in my situation. You might need a different configuration to make it work in your network.

To make this work, you need a recent development core and tools. The process to configure the connection and place the necessary tools is described in detail on the [MEGA65 documentation wiki](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/29327361/Ethernet+tools+mega65+ftp+and+etherload).

Some **good to know points** when working on Linux:

*   For the network setup to work, ensure that on the network connection, for ipv6, the option _link-local_ is enabled. Otherwise you will have an unstable network connection. All other options on the connection can be disabled.
*   After power-cycling the MEGA65, the network connection needs to be re-activated.
*   If you choose to use the serial over USB configuration, be aware that on Linux the logged-in account must be a member of the _dial in_ group before you can use serial connections.

![Image 2: mega65-linux_ipv6.png](https://wiebow.mega65.com/wp-content/uploads/2023/12/image.png)

**The Linux Network Connection settings, showing Link-Local enabled.**

## Build and deploy process

The complete process is automated, using the `make.sh` shell script. I will show the complete script at the end. For now, let’s go through the steps.

### Definitions

The commands to run the tools are defined as variables at the beginning of the script:

```
# make.sh

kickasm="java -jar /home/wiebo/development/mega65/tools/kickass/KickAss65CE02-5.25.jar -vicesymbols -showmem"
c1541="/home/wiebo/development/mega65/tools/c1541"
m65ftp="/home/wiebo/development/mega65/tools/m65tools/mega65_ftp -e "
etherload="/home/wiebo/development/mega65/tools/m65tools/etherload"
```

And I also define the names to use for the project:

```
d81name="WDW.D81"
mainname="main.prg"
```

### Assembling

Calling the assembler with the input file is simple:

`$kickasm main.asm -odir ./bin`
### Disk Image

It is perfectly valid to NOT use a disk image when deploying to the MEGA65. I am doing this to be prepared for when I need multiple files on the same disk. It is perfectly fine to only use the compiled program file.

The `c1541` tool is used to create a disk image and add the main file to it:

```
$c1541 -format "disk,0" d81 "./bin/"$d81name
$c1541 -attach "./bin/"$d81name 8 -write "./bin/"$mainname main
```

More files can be added to the disk image if required.

> If you are running Windows, the [dirmaster](https://style64.org/dirmaster) tool by Style is a great way to manage disk images. Also, the mega65connect tool can help you manage disk file content.

### Run emulated

Xemu emulator is started with the generated file:

`xemu-xmega65 -besure -prgmode 65 -prg "./bin/"$mainname`
Note: In the future I want to mount the disk image as well, but for now I don’t need this.

### Run on hardware

The disk image is copied to the MEGA65 SD card:

`$m65ftp -c "put ./bin/"$d81name -c "quit"`
And mounting the disk image, while also pushing the main file into RAM for a quick startup:

`$etherload -5 -m $d81name  -r "./bin/"$mainname`
Note: The `-5` option is required to force a reboot after the disk image is loaded. Not doing this will result in a hanged machine.

If you do not use a disk image, omit the **-m** parameter and do not use the mega65_ftp tool.

### The complete bash file

This build system requires the file `make.sh` in the same location as the main source file, so I create one for each project, and modify as needed.

Here is the complete content of the Bash file, which has to be given **execute** permissions:

```
# make.sh

kickasm="java -jar /home/wiebo/development/mega65/tools/kickass/KickAss65CE02-5.25.jar -vicesymbols -showmem"
c1541="/home/wiebo/development/mega65/tools/c1541"
m65ftp="/home/wiebo/development/mega65/tools/m65tools/mega65_ftp -e "
etherload="/home/wiebo/development/mega65/tools/m65tools/etherload"

d81name="WDW.D81"
mainname="main.prg"

echo assembling code!
$kickasm main.asm -odir ./bin 

echo making disk image
$c1541 -format "disk,0" d81 "./bin/"$d81name

echo copying program to disk image
$c1541 -attach "./bin/"$d81name 8 -write "./bin/"$mainname main
# note: add more if the project requires more files.

echo launch xemu
xemu-xmega65 -besure -prgmode 65 -prg "./bin/"$mainname

echo deploying disk to mega65
$m65ftp -c "put ./bin/"$d81name -c "quit"

echo running prg on the mega65
$etherload -5 -m $d81name  -r "./bin/"$mainname
```

## Testdrive

After setting up my cross development system, a test is needed to verify that everything works.

I’ve written this small test program. The first section of the code is a BASIC program, and the rest is a print “HELLO WORLD” statement.

> The directive `.cpu _45gs02` is required in the `main.asm` source file to switch to the correct instruction set.

```
// the simplest MEGA65 test

		.cpu _45gs02

		* = $2001

		.word basend 	        // next BASIC line
		.word 1206 	        // line #
		.byte $fe,$02,$30	// BANK 0
		.byte $3a,$9e		// :SYS
		.text toIntString(start)// address as string
		.byte 0 		// end of line
basend:	        .byte 0,0 		// end of basic

// -------------------------------------------

		* = $2011
start:
		lda #$03
		sta $d020

		ldx #$00
loop:
		lda string,x
		beq done
		jsr $ffd2
		inx
		jmp loop
done:
		jmp *

string:		
		.text "HELLO WORLD"
		.byte 0
```

After running the Build system, the Emulator is started with the program running, and when I close the emulator, the disk and program file is sent to the MEGA65 and started. Success!!

Here is the log from Sublime Text showing all the steps. 3 seconds for this run. Nice!

```
assembling code!
//------------------------------------------------------
//   65CE02/45GS02/HUC6280 added by Jesper Gravgaard    
//------------------------------------------------------
//------------------------------------------------------
//         Kick Assembler v5.25 by Mads Nielsen         
//------------------------------------------------------
//------------------------------------------------------
Output dir: /home/wiebo/development/mega65/Test/./bin
parsing
flex pass 1
flex pass 2
flex pass 3
Output pass
Writing prg file: main.prg

Memory Map
----------
Default-segment:
  $2001-$2010 Unnamed
  $2011-$2032 Unnamed

Writing Vice symbol file: main.vs
making disk image
formatting in unit 8 ...
copying program to disk image
writing file `MAIN.PRG' as `MAIN' to unit 8
launch xemu
deploying disk to mega65
2023-12-31T12:15:02.059Z NOTE SD card is SDHC

Uploaded 0 bytes.
Uploaded 66048 bytes.
Uploaded 131584 bytes.
Uploaded 197120 bytes.
Uploaded 262656 bytes.
Uploaded 328192 bytes.
Uploaded 393728 bytes.
Uploaded 459264 bytes.
Uploaded 524800 bytes.
Uploaded 590336 bytes.
Uploaded 655872 bytes.
Uploaded 721408 bytes.
Uploaded 786944 bytes.2023-12-31T12:15:03.828Z NOTE reseting MEGA65 and exiting

Uploaded 819200 bytes in 1 seconds (800.0KB/sec)
running prg on the mega65
2023-12-31T12:15:03.830Z NOTE MEGA65 Ethernet Loading Tool 20231223.18-develo-fa53075
2023-12-31T12:15:04.485Z NOTE Sent ./bin/main.prg to fe80::4862:beff:fe36:2b1b on port 4510.
2023-12-31T12:15:04.486Z NOTE Reset to MEGA65 mode
[Finished in 3.3s]
```

## Debugging

The _Matrix Mode Monitor_ is a tool that can be used to troubleshoot and debug programs while running. It will allow you to view and modify the memory of the machine. You can also view CPU register values, force breakpoints, and so on. All this will be something to look into if debugging becomes necessary. And knowing me, it will. The Mega65 Book explains all the commands in Appendix K.

It can be started by pressing `MEGA+TAB`. You can also use the matrix mode debugger in **Xemu** by right-clicking, and selecting **Debug > Advanced / Matrix mode**.

## Concluding

It requires some time to set up, but a Cross Development environment has so many advantages over programming assembly locally that it is worth the time doing so. Still, I will program in BASIC locally on the machine, because that just adds to the retro experience. 🙂

I hope you enjoyed this post, which does show the combined power of modern hardware and tools in combination with this nice retro-like machine. Developing for this machine will be a joy.

Thanks for reading. Leave comments or questions in the reactions and I’ll surely reply or help you along.

## References

1.   [https://gitlab.com/jespergravgaard/kickassembler65ce02/-/releases](https://gitlab.com/jespergravgaard/kickassembler65ce02/-/releases)
2.   [https://www.magic64knight.com](https://www.magic64knight.com/)
3.   [https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/29327361/Ethernet+tools+mega65+ftp+and+etherload](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/29327361/Ethernet+tools+mega65+ftp+and+etherload)
