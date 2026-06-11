# Cross development for the MEGA65

- URL: https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/
- Published: 2023-12-31
- Fetched: 2026-06-11
- Note: near-verbatim capture — the working Linux (Linux Mint) cross-dev pipeline. Paths differ on Windows/macOS but the principles hold.

## Introduction

Setting up a system to program **Assembly** on a PC, then deploy the compiled program to an emulator and to the real MEGA65. *Cross Assembly* = writing/assembling for a CPU other than the dev machine's (e.g. 6502 code on an AMD/Intel PC). Ingredients:

- An assembler
- A text editor (preferably with syntax highlighting)
- A build system to: assemble the program, create a disk image containing it
- Deploy to: an emulator (quick iteration) and the MEGA65 (physical connection)
- A debugger

## System setup

### File system
Dev files in `~/development/mega65`, with a `tools` sub-folder and a `project` folder per project.

### Assembler
**Kick Assembler**, specifically the [modified 65CE02 fork](https://gitlab.com/jespergravgaard/kickassembler65ce02/-/releases) that supports the 45GS02 instruction set. Place `KickAss65CE02-5.25.jar` in `~/development/mega65/tools/kickass/`. Ensure **Java** is installed (`java --version`).

### Disk image
Kick Assembler can only make `.D64` (not yet mountable on MEGA65). Use `c1541` (ships with **VICE**) to create `.D81` images — install VICE via Software Manager, copy `c1541` from `/usr/bin` to `tools`.

### Emulator
**Xemu** ([repo](https://github.com/lgblgblgb/xemu), [MEGA65 quickstart wiki](https://github.com/lgblgblgb/xemu/wiki/MEGA65-quickstart)). Needs the `mega65.rom` file (FileHost member area, or the MEGA65's internal SD card) — ideally the same ROM as the physical machine.

### Text editor
**Sublime Text** with a 45GS02 language file ([wiebow's fork](https://github.com/wiebow/M65_KickAsm_Macros)). Place `KickAssembler (Mega65).sublime-syntax` in `~/.config/sublime-text/Packages/User`. Create a build system (**Tools > Build System > New Build System…**):

```
{
	"shell_cmd": "./make.sh"
}
```

Name it `Kickassembler (M65)`; then `CTRL-B` runs the script.

### Physical deployment — two options
- **Serial:** via JTAG (serial over USB). On Linux the account must be in the *dial in* (dialout) group.
- **Network:** a cable directly between PC and MEGA65 — the author's choice ("the way forward," faster than serial). Uses **Link-Local IPv6**. Setup documented on the [MEGA65 Ethernet-tools wiki page](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/29327361/Ethernet+tools+mega65+ftp+and+etherload).

**Linux good-to-know:**
- For the network setup, enable IPv6 *link-local* on the connection or it'll be unstable; all other options can be disabled.
- After power-cycling the MEGA65, re-activate the network connection.

## Build and deploy process — `make.sh`

Tool variables:

```
kickasm="java -jar /home/wiebo/development/mega65/tools/kickass/KickAss65CE02-5.25.jar -vicesymbols -showmem"
c1541="/home/wiebo/development/mega65/tools/c1541"
m65ftp="/home/wiebo/development/mega65/tools/m65tools/mega65_ftp -e "
etherload="/home/wiebo/development/mega65/tools/m65tools/etherload"
d81name="WDW.D81"
mainname="main.prg"
```

- **Assemble:** `$kickasm main.asm -odir ./bin`
- **Disk image:**
  ```
  $c1541 -format "disk,0" d81 "./bin/"$d81name
  $c1541 -attach "./bin/"$d81name 8 -write "./bin/"$mainname main
  ```
  (Windows: [dirmaster](https://style64.org/dirmaster) or mega65connect for disk management.)
- **Run emulated:** `xemu-xmega65 -besure -prgmode 65 -prg "./bin/"$mainname`
- **Run on hardware:**
  ```
  $m65ftp -c "put ./bin/"$d81name -c "quit"        # copy D81 to SD card
  $etherload -5 -m $d81name -r "./bin/"$mainname    # mount + push to RAM, reboot
  ```
  The **`-5` option is required** to force a reboot after the disk image loads — without it the machine hangs. If not using a disk image, omit `-m` and skip mega65_ftp.

### Complete make.sh

```
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

echo launch xemu
xemu-xmega65 -besure -prgmode 65 -prg "./bin/"$mainname

echo deploying disk to mega65
$m65ftp -c "put ./bin/"$d81name -c "quit"

echo running prg on the mega65
$etherload -5 -m $d81name -r "./bin/"$mainname
```

## Test program

The directive `.cpu _45gs02` is required to switch to the correct instruction set. The program has a BASIC stub launcher at $2001 and code at $2011:

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
basend:	.byte 0,0 		// end of basic
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

Full edit-build-run loop (assemble → D81 → Xemu → mega65_ftp upload → etherload) completes in **3.3 seconds**. Etherload reports sending to the MEGA65's IPv6 link-local address (e.g. `fe80::...`) on port 4510.

## Debugging

The **Matrix Mode Monitor** views/modifies memory, shows CPU registers, and sets breakpoints. Start with `MEGA+TAB` on hardware, or in Xemu via right-click → **Debug > Advanced / Matrix mode**. Commands documented in the MEGA65 Book, Appendix K.

## References

1. https://gitlab.com/jespergravgaard/kickassembler65ce02/-/releases (Kick Assembler 65CE02 fork)
2. https://www.magic64knight.com
3. https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/29327361/Ethernet+tools+mega65+ftp+and+etherload (Ethernet tools setup)
