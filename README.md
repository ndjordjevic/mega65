# Learning the MEGA65

My personal journey learning the **[MEGA65](https://mega65.org)** — the open-source revival of the never-released Commodore 65. This repo is where I collect, organize, and make sense of everything I'm picking up: the hardware, BASIC 65, 45GS02 assembly, the VIC-IV chipset, cross-development toolchains, and the wider community.

It doubles as a knowledge base that an AI assistant can read, so I can ask questions and get answers grounded in real sources instead of guesswork.

## What I'm learning here

- **The machine** — board revisions, the Artix-7 FPGA core, memory map, Hypervisor
- **BASIC 65** — the built-in language, graphics/sound commands, on-device editing
- **45GS02 assembly** — the CPU, registers, the monitor, raster interrupts
- **VIC-IV graphics** — character modes, FCM/NCM, sprites, the Raster Rewrite Buffer
- **SID sound** — the 4 SID chips, ADSR, BASIC sound commands
- **Cross-development** — Xemu, assemblers (ACME, Kick), C (llvm-mos, Calypsi), file transfer

`wiki/overview.md` is the running synthesis of what I've learned; `wiki/index.md` lists every source.

## How it's organized

```
wiki/         ← my notes: summarized, cross-linked pages per source
  index.md      start here — full list of what's covered
  overview.md   cross-source synthesis of the big picture
  sources/      one page per source I've studied
raw/          ← the original material, captured so I can always check it
  web/          fetched articles & sites (e.g. all of Dan Sanderson's Digest)
  github/       code repos, tutorials, the user-guide LaTeX source
  assets/       the official PDF manuals (see raw/assets/README.md)
resources.md  ← catalog of every MEGA65 resource I know about
```

## The tooling underneath

The wiki is built and maintained with **[pin-llm-wiki](https://github.com/ndjordjevic/pin-llm-wiki)**, a small tool that fetches a source, summarizes it into `wiki/`, and keeps an immutable copy in `raw/`. It's just the plumbing — the point of the repo is the MEGA65, not the tool.

- **`AGENTS.md`** — how an AI assistant should answer MEGA65 questions from these files (the protocol: wiki → official spec → resources → web). Shared across Claude Code, Cursor, and Copilot.
- **`CLAUDE.md`** — thin Claude Code adapter that imports `AGENTS.md`.
- **`context-strategy.md`** — why I built the knowledge layer this way.
- **`inbox.md` / `.pin-llm-wiki.yml`** — source queue and config for the tool.

To add or refresh sources, see the [pin-llm-wiki docs](https://github.com/ndjordjevic/pin-llm-wiki). Note: the large PDF manuals and the full LaTeX clone are gitignored — grab the manuals from [files.mega65.org](https://files.mega65.org) (index in `raw/assets/README.md`).
