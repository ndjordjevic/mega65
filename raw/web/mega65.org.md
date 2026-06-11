# mega65.org

## Fetch log
- Inbox URL: https://mega65.org/
- Final URL: https://www.mega65.org/
- Fetched: 2026-06-10
- Pages: 4
- Mode: deep
- Products discovered: 0
- Note: llms.txt and sitemap.xml both 404. /docs redirects to the Confluence wiki (mega65.atlassian.net); /try redirects to the Confluence emulator guide — both captured below via Jina Reader. Giant Atlassian media-CDN image URLs replaced with [image] markers; all text preserved.

## Discovery audit
- Candidates from llms.txt (depth 1/2/3): none — llms.txt 404
- Candidates from sitemap.xml: none — sitemap.xml 404
- Candidates from landing page: File Host (files.mega65.org), GitHub (github.com/MEGA65 — org link), XEMU MEGA65 Emulator (github.lgb.hu/xemu — third-party site), Documentation (/docs → Confluence), Alternative Cores (cores.mega65.org), Discord, Forum 65, YouTube, Twitter, Reddit
- Candidates from GitHub URLs: github.com/MEGA65 (org root, not repo root — rejected); github.com/MEGA65/mega65-examples (appears on docs landing page only, not landing page)
- Classified as products: none — the site presents one product, the MEGA65 computer itself
- Classified as excluded: Discord/Forum 65/YouTube/Twitter/Reddit (community channels), Documentation (docs section), File Host (download service for the same product), Alternative Cores (content catalog for the same hardware), XEMU (third-party emulator with its own site/repo, queued separately in this wiki)
- Classified as sub-section of existing product: n/a
- Conclusion: single-product site → products = [], single-product deep mode; companion_github_url = null (landing page links the GitHub org, not a repo root)

## Landing page — https://www.mega65.org/

# MEGA65 - 8-Bit Computer

Navigation — Explore:
- File Host
- GitHub
- XEMU MEGA65 EMULATOR
- Documentation
- Alternative Cores

Navigation — Community:
- Discord
- Forum 65
- YouTube
- Twitter
- Reddit

Core messaging: The MEGA65 is described as a "21st century realization of the C65" offering around 40x faster performance than a C64 while maintaining compatibility. Key selling points:
- Completely open-source design
- C64 and C65 compatibility
- Mechanical keyboard with HD output
- Dual SD card support and Ethernet
- Real 8-bit computer (not an emulator)
- Built-in floppy drive

Featured capabilities: supports "MEGA-OS hypervisor and BASIC 65 including freezer, VFAT32 file system, 4 SIDS, GEOS 65" plus additional features.

Community recognition: Notable figures praise the device, with one calling it "an absolutely beautiful machine," another: "The Commodore 65 lives again!"

Manufacturing partners: MOULDS TEAM, Trenz Electronic, GMK, Hintsteiner Group, KEVAG Telekom.

Additional resources linked:
- Dan's MEGA65 Digest (monthly newsletter)
- Paul Gardner-Stephen's development blog (c65gs.blogspot.com)
- MEGA Museum official website

## Docs — https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21331992/Documentation+-+Landing+Page
(reached via redirect from https://mega65.org/docs)

The MEGA65 project has multiple locations that can be perused for documentation, they will be outlined below:

### PDF manuals

We have a suite of PDFs with varying content that will be described here:

- **The MEGA65 User's Guide** — Provides an introduction to the MEGA65, and a condensed BASIC 65 command reference. Download: mega65-userguide.pdf (https://files.mega65.org/?id=a5081244-a976-4a21-9153-27cca13fd613)
- **The MEGA65 BASIC 65 Reference** — Comprehensive documentation of all BASIC 65 commands, functions and operators. Download: mega65-basic65-reference.pdf (https://files.mega65.org/?id=42d0f1f9-610a-45f9-bad1-9502f0e6eb7d)
- **The MEGA65 Developer's Guide** — Information for developers who wish to write programs for the MEGA65. Download: mega65-developer-guide.pdf (https://files.mega65.org/?id=ffd575e5-5d9c-47ff-b553-fcec80fd77a3)
- **The MEGA65 Complete Compendium** (Also known as The MEGA65 Book) — All volumes in a single huge PDF for easy searching, plus additional chapters in progress. 1,433 pages and growing! Download: mega65-book.pdf (https://files.mega65.org/?id=d668168c-1fef-4560-a530-77e9e237536d)

Jenkins will build all PDFs from the latest source, and upload successful builds to the Filehost links above. Build status: https://builder.mega65.org/job/mega65-user-guide/job/master/

### retroCombs video User's Guide

retroCombs is producing a video companion to the MEGA65 User's Guide, 2nd edition:

- Chapter 1: MEGA65 Intro: The Retro Journey Begins — https://www.youtube.com/watch?v=UUVOtkLP-eY
- Chapter 2: MEGA65 Setup: Unbox to "READY" Prompt — https://www.youtube.com/watch?v=HOJIwK7CqMY
- Chapter 3: MEGA65 Keyboard, Editor & Freezer: The Basics — https://www.youtube.com/watch?v=kKGhYTJlSuw
- Chapter 4: MEGA65 Configuration Utility and SD Cards — https://www.youtube.com/watch?v=C-PNB9rlzV4
- Chapter 5: MEGA65 Upgrades: Core, ROM, & System Files! — https://www.youtube.com/watch?v=XkDss1mj5CU
- Chapter 6: MEGA65 Using Disks and Disk Images — https://www.youtube.com/watch?v=lw7o2X91Zt4

### Filehost articles

Individual articles written by MEGA65 owners pertaining to their specific user experiences and knowledge that they would like to share in an article that they maintain sole control over:
- MEGA65 Filehost (https://files.mega65.org/), then select "Articles"

### Wiki

A location for documenters within the community to share their knowledge in a collaborative manner, allowing for multiple editors to contribute to the same article:
- https://mega65.atlassian.net

### Dan's MEGA65 Welcome Guide

A good introduction for new owners to get better acquainted with their new machines!
- MEGA65 Welcome Guide — https://dansanderson.com/mega65/welcome/

### Dan's MEGA65 Digest

Don't have the time to spare to follow the latest news on our Discord chat server? Then subscribe to Dan's MEGA65 Digest to receive a newsletter every month or so on the latest MEGA65 news!
- Dan's MEGA65 Digest | Substack — https://m65digest.substack.com/

### MEGA65 Discord Server

Got a question you can't find the answer to in any of the above? Then jump onto the Discord server and give us a ping there! We've got a vibrant, friendly community that will try get you the answers you're looking for!
- https://mega65.org/chat

### Code samples

Looking for help getting started with programming? Want some ideas for your programs? Got a snippet of code that you think others might find useful? Try these resources.
- GitHub - MEGA65/mega65-examples: A gathering point for community created software examples for the MEGA65. — https://github.com/MEGA65/mega65-examples

### BASIC 65 Referenzhandbuch

Günther Reiter maintains a German-language version of the BASIC language reference. Get it from his website:
- https://65site.de/downloads/MEGA65_BASIC_65_Referenzhandbuch.pdf

## Curious about the MEGA65? Want to try the emulator? — https://mega65.org/try
(redirects to https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/12648455/...)

For folks that are curious about the MEGA65, that want to browse and explore its universe through an emulator first, here's some links to help you out on your journey:

### Getting the Xemu emulator and MEGA65 ROM

- Xemu MEGA65 emulator available here: https://github.lgb.hu/xemu/
  - Usually it's best for most users to use the stable '**master**' version of xemu
  - Though if you're an early user of the latest ALL_INTROS, I suggest the latest '**next**' version of xemu
- Sourcing a MEGA65 ROM for the emulator can be tricky (licensing issues)
- There is a pathway available to patch a C65 ROM into a MEGA65 ROM
- In more recent times, a few community members have contributed scripts that will automate the retrieval of C65 rom over the net and patching it into a M65 rom. If you're curious to try, take a look at:
  - MakeROM Windows Batch (https://files.mega65.org/?id=50a30f42-4fc2-409b-97d3-b33a7d2a1e10)
  - MakeROM Linux version (https://files.mega65.org/?id=04ce211a-942b-4c6e-b091-5a4f9c44538b)
- See Retrocombs' walkthrough videos for advice:
  - Install on Mac OSX: Install and run the MEGA65 emulator, Xemu, on Mac OS X — https://youtu.be/8PbSxkYVD8I
  - Install on Chromebook: Install the MEGA65 Emulator on a Chromebook! — https://youtu.be/z65O6bxIkaY
  - For windows: reference the vids above (it's fairly similar)
  - Patching a C65 ROM into a MEGA65 ROM: MEGA65: Patch a Commodore 65 ROM to use with the XEMU Emulator — https://youtu.be/volGqBd143k

### Try out existing software

- Try out existing programs available for download on the MEGA65 filehost: https://files.mega65.org/

### How do I use .prg and .d81 files with xemu?

**Option 1**: Drag'n'drop .prg and .d81 files onto the xemu window. Upon doing so, a popup window will appear. Typically you would do as follows:
- For prg files: click "**Run/injecting as PRG**"
- For .d81 files: click "**Mount as D81**"

**Option 2**: right-click via the context menu.

**Option 3**: Use the "**HDOS virtualisation**" option. Alternatively, run xemu from the command-line with the `-hdosvirt` argument. Then locate the HDOS folder, then drop your PRG/.D81 files within the "**hdos**" folder. Then back in xemu:
- For PRG files, type: `DLOAD "FILE.PRG",U12`
- For D81 files, type: `MOUNT "MYDISK.D81"` and can then do any of the following:
  - do a `DIR` to see the contents within.
  - You can press `SHIFT` + `RUN-STOP` to load the first file on the disk
  - If the disk contains an `AUTOBOOT.C65` file, you can type `BOOT` to run it
  - You can use the cursor keys to move to the start of any PRG file within the `DIR` listing and type `/` followed by `RETURN` key to load and run it

NOTE: When using this option, it's probably best to rename all your files to be: all uppercase, DOS 8.3 filenames. E.g. "GNG.D81" (and not "Ghosts n Goblins.d81")

### I'd like to try run "ALL_INTROS" package in xemu!

UPDATE: We've recently released our **ALL_INTRO DISKS zip package** containing **ALL** intro disks from the past years!

This is a great way to sample many programs created by the community quickly via a friendly menu system. As of **2025**, it gives you access to about **263 software titles**! [image] [image] [image] [image]

**Download links**:
- Public edition: https://files.mega65.org?id=all-intros-public — GEOS with just TopDesk only
- Private edition (for registered MEGA65 owners only): https://files.mega65.org?id=all-intros — GEOS with TopDesk + bundled applications; extras: MEGA65.ROM, MEGA650.ROM (openrom), MEGA651.ROM (c65 rom) and CHARSET.M65

If you'd like to try the ALL_INTROS collection via the MEGA65 emulator, recommended approach:
- Un-zip the "**ALL_INTROS - Public.zip**" file and place all items within its "**sdcard-files/**" folder into your "**hdos**" folder as per option 3 described earlier
- Drop a copy of your "**MEGA65.ROM**" into this "hdos" folder too (the latest Intro Disk #4 will need to load it from here)

### Configuring Xemu for ALL_INTROS package

- Run xemu and turn on HDOS support
- Recommended: "**Input devices >> Use F9..F11 as hotkeys**" — allows you to reset xemu via **F10** key to go back to the Intro Disk menu after you try each program.
- Recommended: "**Input devices >> Reset hotkey type >> HYPPO**" so that these F10 resets work similar to how the real machine resets via its physical reset button.
- Recommended: save settings via "**Configuration >> Save config as default**" — assures these settings are used automatically the next time you start xemu; it will start up with hdos turned on and load the Main Menu via the default MEGA65.D81 image.
- After you try running a program on the menu, xemu should let you jump back to the menu with `F10` (reboot). On occasions it fails (due to a program that needed to mount another disk), try press `F9` instead (shutdown), and re-run xemu.

### Joystick support within Xemu

- **USB Joysticks**: USB joysticks do work fine in xemu. [image] [image]
- **Joystick emulation via keyboard — Via Numeric Keypad**: By default, xemu uses the numeric keypad to emulate the joystick on port 2. To swap over to port 1, press the numeric keypad's "Enter" key.
- **Via Cursor Keys**: As some keyboards don't have a numeric keypad (such as on laptops), an alternative is available to set the cursor keys as the joystick. Right-click and go to "**Input Devices >> Cursor keys as joystick**". If you need to swap between joy port 1/2, go to "**Input Devices >> Swap emulated joystick port**"

### Want to learn more?

- Also worth having a browse of the free pdf 'mega65-book' manual, available here: https://files.mega65.org/manuals-upload
- Have a chat and ask questions on:
  - Forum64.de: https://mega65.org/forum
  - Discord: https://mega65.org/chat

### Ok, I've tried all that, now I want the real thing!

After exploring, if you find yourself itching to purchase a MEGA65, head to the Trenz website:
- Order Full Product: MEGA65 - highly advanced C64 and C65 compatible 8-bit computer — https://shop.trenz-electronic.de/en/TE0765-06-T001CK-MEGA65-highly-advanced-C64-and-C65-compatible-8-bit-computer?c=564
- Order separate parts: https://shop.trenz-electronic.de/en/Products/MEGA65/
- (don't worry about the `In Stock: 0` text, as batch#2 is on the way)

## MEGA65 Alternative Cores — https://cores.mega65.org/

### What are "alternative" MEGA65 cores?

From day one, the MEGA65 was designed to be the spiritual successor of the legendary Commodore 65. To realize that goal and stay future proof, the MEGA65 is based on something called a FPGA - "Field-programmable Gate Array". Think of it as "programmable hardware". Usually the CPU inside a computer is pure hardware: It is manufactured and can't be changed by a user. An FPGA can be (within technical limits) any CPU you imagine and so can, like a chameleon, literally become a C64, Arcade Machine or Gameboy.

This is not what people usually refer to as **emulation**. An Emulator is a program that runs on a CPU and translates each command into instructions the CPU can understand. It's like have a translator at your side when you do not speak the language. An FPGA runs the code as if it IS that CPU. The analogy is that you learn the language yourself and can speak it like your mothers tongue.

Recreation of retro hardware via FPGA is not perfect. While most of the weirdest details can be identical to a real machine, there still are some obscure effects that might have fallen through the cracks. Still, because the timing of all the components in the FPGA is much closer to the real thing than in emulation, you usually get an extremly high fidelity.

So, an "Alternative" Core is basically a new language for the FPGA inside the MEGA65. It turns it into a different system. The MEGA65 has seven "slots" so you can immediately switch between them, and you can reprogram those slots with any of the Cores seen on these pages.

Oliver Graf aka _lydon_ made a great YouTube explanation video (https://youtu.be/9Ib7z64z9N4) about recreating retro systems using FPGAs, about the awesome MiSTer project and about the difference between MiSTer and the equally awesome MEGA65.

### When is the next Core coming out?

All Core development is done by enthusiasts with day-time jobs who do awesome work for free. Because of this, your expectation should be that a Core may NEVER be released or updated. There are NO promises for an upgraded C64 Core, a R6-compatible Gameboy-Core, an Amiga-Core or more Arcade-Cores. People are working on those in their spare time, everything is a labour of love and the purchase of the MEGA65 does not entitle you to any Core (but the original MEGA65 Core).

### Can I run other FPGA-based Cores on MEGA65?

Unfortunately you can not take FPGA Cores written for MiSTer or the Analogue Pocket and run them straight on the MEGA65, but it is possible to convert Cores written for other systems. Please refer to the page Creating new Cores (https://kugelblitz360.github.io/m65-altcores/creating-new-cores-for-mega65.html) for more details.

### Can I add a core to this list?

I am checking the MEGA65 filehost regularly for Core updates and try to update this list within a matter of days, if not hours. If for any reason I have missed an update or you have a release that is not available on the file host, write me an E-Mail to boris@dreisechzig.net. Updates on Work-in-Progress are also very welcome.

### I have additional questions!

The best place to discuss is the MEGA65 Discord and the specific channel for Alternate Cores: https://discord.com/channels/719326990221574164/1177364456896999485
Additionally you can try the MEGA65 discussion board (mainly in German language): https://www.forum64.de/index.php?board/457-mega65/

### Where are the cores?

- Home Computers — https://kugelblitz360.github.io/m65-altcores/computer-cores.html
- Arcade Games — https://kugelblitz360.github.io/m65-altcores/arcade-cores.html
- Game Consoles — https://kugelblitz360.github.io/m65-altcores/game-console-cores.html
