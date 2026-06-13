---
type: source
source_url: https://www.m-e-g-a.org/
tags: [mega65-community, museum, game-preservation, megasputm, scumm-engine, retrogaming, rrb-graphics, calypsi, community-events, blog-index]
related: [mega65.org, dansanderson.com, retrocogs.mega65.com]
product: m-e-g-a
detail_level: standard
created: 2026-06-13
updated: 2026-06-13
---

MEGA eV (Museum of Electronic Games & Art) is a German museum organization preserving and showcasing electronic games and digital art. The MEGA65 retro computer is a central focus of the organization's current activities — they host community workshops, cover MEGA65 news, and are home to the MegaSPUTM project, a community-built SCUMM engine re-implementation that runs classic LucasArts adventure games (Maniac Mansion, Monkey Island) on MEGA65 hardware. The organization provides an independent community hub for MEGA65 news and events beyond the official channels documented in [[mega65.org]] and [[dansanderson.com]]. The **## Post index** section at the bottom of this page lists all 117 blog posts (2010→2026) with a one-line gloss each, so the site's news archive is searchable from inside the wiki.

_All claims below are sourced from ../../raw/web/m-e-g-a.org.md unless otherwise noted._

## What it does

The site serves as a news blog and community hub for MEGA65 enthusiasts, run by the MEGA eV museum organization in Germany. It covers MEGA65 hardware availability and batch shipping news, community workshops for new users, the MegaSPUTM software project, and general retrogaming events the organization hosts.

## Key features

- **MEGA65 community hub:** news coverage of MEGA65 batch shipping, firmware updates, new core releases, and community events. The December 2022 article announced 920 MEGA65 computers in the wild with the 2nd batch shipping.
- **Community workshops:** introductory MEGA65 workshops for beginners, C64 fans, and returnees (January 2026 example) — a community onboarding resource complementing the written guides at [[dansanderson.com]].
- **MegaSPUTM:** community SCUMM engine re-implementation for MEGA65 by developer kibo (GitHub: `ki-bo/megasputm`). Runs original LucasArts adventure game assets on MEGA65 hardware. Technical highlights:
  - Exploits MEGA65-specific hardware: multi-layer RRB graphics, digital audio samples, fast load times, mouse input, real floppy disk compatibility
  - Performance exceeds the Amiga 500 version of Maniac Mansion
  - Built with the Calypsi C compiler (MEGA65-targeted)
  - Developer M3wP (GitHub: `M3wP`) collaborating on a 256-color Monkey Island version
- **Archive and events:** broader museum activities include retrogaming tournaments (Tekken 3 at BieberLAN), gaming history events ("Spring Loot"), and preservation of consoles, home computers, handhelds, and software.

## Architecture and concepts

The organization operates a WordPress site (`megaeleven` theme) covering multiple sections: News, MEGA collection, Archive (consoles, computers, handhelds, software), Research & Education, Exhibitions, and Media. The MEGA65 content is distributed across news posts and the MegaSPUTM project page (`/megasputm/`). No structured docs section or llms.txt.

MegaSPUTM's technical architecture: the engine re-implements the SCUMM interpreter in C (Calypsi compiler), using MEGA65 hardware registers directly for RRB graphics (see [[retrocogs.mega65.com]] for RRB technical background), SID/digital audio, and standard MEGA65 disk I/O. Original game data files from the commercial releases are required — the engine ships without copyrighted assets.

## When to use

- When looking for community event information (workshops, gaming events) run by the German MEGA65 community.
- When researching MegaSPUTM — the only SCUMM engine implementation for MEGA65 and a showcase of RRB graphics and Calypsi C compiler usage.
- For MEGA65 historical news (batch shipping dates, core release announcements) from a community perspective.

## Ecosystem

The site references [[dansanderson.com]] (Dan's Welcome Guide) and the MEGA65 Discord as complementary resources for new owners. MegaSPUTM uses the Calypsi C compiler (distinct from the more common [[cc65-cc65]] / [[MEGA65-mega65-libc]] toolchain). The RRB graphics technique behind MegaSPUTM is documented in [[retrocogs.mega65.com]] and [[RetroCogs-Mega65Tutorials]].

## Post index

All 117 posts from the MEGA eV blog (WordPress main feed, `/feed/?paged=N`), grouped by year, newest first. This is a general electronic-games museum blog, so posts range from MEGA65 news (releases, batches, MegaSPUTM, getting-started workshops) to broader retrogaming and museum-event coverage. Each gloss is the cleaned opening sentence of the post's own RSS excerpt — the author's framing, not an editorial rewrite; a few gallery posts have only pagination text as their excerpt. Follow any permalink for the full post.

### 2026 (2 posts)

- **[Retrogaming at 50th BieberLAN](https://www.m-e-g-a.org/retrogaming-at-50th-bieberlan/)** (2026-06-07) — On Saturday morning at 8:30 a.m., we began setting up in the still quiet Frankfurt ice sports arena — many LAN attendees were still enjoying their well-deserved sleep.
- **[Getting started with MEGA65](https://www.m-e-g-a.org/getting-started-with-mega65/)** (2026-01-16) — Starter course for MEGA65 newbies – User meeting for MEGA65 family & friends Are you new to MEGA65 or want to finally get started?

### 2025 (3 posts)

- **[Tube Love](https://www.m-e-g-a.org/crt-love/)** (2025-04-27) — While gathering our strength for the upcoming archive activities, we physically exhausted ourselves lifting old CRT (Cathode Ray Tube) monitors, but were immediately rewarded by…
- **[MegaSPUTM: Maniac Mansion Enhanced for the MEGA65](https://www.m-e-g-a.org/megasputm/)** (2025-01-14) — The classic adventure Maniac Mansion is now playable on the MEGA65 thanks to MegaSPUTM, a re-implementation of the SCUMM engine by community member kibo.
- **[MEGA Move](https://www.m-e-g-a.org/mega-move/)** (2025-01-12) — We are delighted that MEGA e.V.

### 2024 (2 posts)

- **[Ambassadors](https://www.m-e-g-a.org/ambassadors/)** (2024-11-18) — For the first time in history the MEGA65 is in stock and can be ordered directly, including spare parts!
- **[Spring Loot](https://www.m-e-g-a.org/spring-loot/)** (2024-04-26) — MEGA e.V.’s Spring Loot Event in Darmstadt, Germany, on March 23rd, 2024, was a nostalgic trip for gaming enthusiasts.

### 2023 (6 posts)

- **[Vintage Computing Festival Berlin](https://www.m-e-g-a.org/vintage-computing-festival-berlin/)** (2023-10-12) — Next weekend (14.10.
- **[Classic Computing 2023](https://www.m-e-g-a.org/classic-computing-2023/)** (2023-09-23) — MEGA will be attending the Classic Computing 2023 event in Dietzenbach (near Frankfurt am Main / Germany) next weekend.
- **[mega.museum](https://www.m-e-g-a.org/mega-museum/)** (2023-06-30) — We have reached official museum status and visibility and aquired the mega.museum domain.
- **[C64 for MEGA65](https://www.m-e-g-a.org/c64-for-mega65/)** (2023-06-25) — MJoergen and sy2002 just released the Commodore 64 for MEGA65 core version 5 and their MiSTer2MEGA65 framework version 1.0.
- **[Open Doors Extension](https://www.m-e-g-a.org/open-doors-extension/)** (2023-01-07) — We received a lot of feedback to re-open doors after the MEGA65 launch event and open doors day – so here is an extension!
- **[Zzap64!](https://www.m-e-g-a.org/zzap64/)** (2023-01-04) — Most if not all C64 fans will remember the british cult computer magazine Zzap!64 which recently was reborn through a Patreon campain, not only as a digital download with great…

### 2022 (5 posts)

- **[MEGA65 batch two](https://www.m-e-g-a.org/mega65-batch-2/)** (2022-12-10) — Despite the worldwide situation the 2nd batch of MEGA65 computers is shipping in this a busy yet successful year – making it a total of 920 MEGA65 out in the wild!
- **[10th anniversary & MEGA65 release](https://www.m-e-g-a.org/10th-anniversary-mega65-release/)** (2022-08-31) — The event on Saturday, August 27th 2022 delighted many hearts and the MEGA65 release was a complete success.
- **[10th anniversary preparations](https://www.m-e-g-a.org/10th-anniversary-preparations/)** (2022-08-01) — Update 23rd of August: The exhibition is fully set up!
- **[BASIC 65 – from dead horse to stallion](https://www.m-e-g-a.org/basic-65-from-dead-horse-to-stallion/)** (2022-02-02) — Once the team had official permission to use the C65 ROM for the MEGA65 project, Bit Shifter decided to take on the task and look at the ROMs source files.
- **[First physical MEGA65 release](https://www.m-e-g-a.org/first-physical-mega65-release/)** (2022-01-07) — One of the most captivating science fiction stories surfaced in 2018 for classic 8-bit and 16-bit systems when Berlin based author Stefan Vogt released his game Hibernated with…

### 2021 (5 posts)

- **[MEGA65 Pre-orders](https://www.m-e-g-a.org/mega65-pre-orders/)** (2021-10-19) — After seven years of work the biggest project MEGA ever started has reached an important milestone: The MEGA65 desktop computer can now be pre-ordered and production has begun!
- **[Commodore 1565](https://www.m-e-g-a.org/commodore-1565/)** (2021-06-25) — Here at MEGA one mission is to preserve or even recreate objects, knowledge and code from the short but fragile digital history of mankind, save them and their creators from being…
- **[C-One](https://www.m-e-g-a.org/c-one/)** (2021-02-19) — Digital archeology of a different kind: Perhaps a pioneer for computers like the MEGA65, the C-One claimed to be the very first reconfigurable FPGA computer.
- **[Interactive Fiction](https://www.m-e-g-a.org/interactive-fiction/)** (2021-02-08) — With game graphics becoming more and more realistic, there has been a reanaissance of classic text adventures lately.
- **[ZX-UNO 65](https://www.m-e-g-a.org/zx-uno-65/)** (2021-01-29) — The Sinclair ZX Spectrum was one of the most popular 8-bit computers worldwide.

### 2020 (5 posts)

- **[C256 FOENIX](https://www.m-e-g-a.org/c256-foenix/)** (2020-12-17) — After quite a journey in these troubled times, a FOENIX has arrived at the MEGA archive.
- **[The Retro Wars](https://www.m-e-g-a.org/the-retro-wars/)** (2020-09-07) — With Retro Computing becoming more and more popular, a lot of different players have entered the game.
- **[DIGILOI](https://www.m-e-g-a.org/digiloi/)** (2020-08-26) — Limitations spark creativity – this is a known fact in the demo scene and also applies to real life.
- **[MEGA65 DevKit](https://www.m-e-g-a.org/mega65_devkit/)** (2020-06-17) — In the making for full 5 years now, the MEGA65 is finally ready for pre-orders in form of a Development Kit.
- **[Tatort Tabletops](https://www.m-e-g-a.org/tatort-tabletops/)** (2020-02-10) — The “Tatort Dortmund” episode “Monster” was broadcast on 02.02.2020.

### 2019 (1 post)

- **[MEGA roundup](https://www.m-e-g-a.org/mega-roundup-2019-1/)** (2019-06-08) — It might look as if we are taking a time off as there has not been a post for several weeks.

### 2018 (7 posts)

- **[Portable Classics](https://www.m-e-g-a.org/portables-allerlei/)** (2018-11-18) — For “Digital Day for All” during the 1st Digital Week in Leer, we presented various portable computers and electronic devices from the past.
- **[Vintage Text Computing & Gameboy meets Lagerfeuer](https://www.m-e-g-a.org/vintage-text-computing/)** (2018-11-18) — At the DARIAH-DE Grand Tour 2018, we successfully proved that already more than 30 years ago computers not just allowed to write adventures, but more importantly to interactively…
- **[MEGA65.org updated](https://www.m-e-g-a.org/mega65-org-updated/)** (2018-09-18) — The new MEGA65.org website is online!
- **[MEGA65 keyboards](https://www.m-e-g-a.org/mega65-keyboards/)** (2018-09-09) — Summer break is over so we are again busy working on the MEGA65.
- **[Art et jeux vidéo](https://www.m-e-g-a.org/art-et-jeux-video/)** (2018-06-12) — The newly published book “Art et jeux vidéo” shows our T42 – Tennis for Two and beautifully portrays the aspect of art in video games of the last decades.
- **[Programming Basics (squared)](https://www.m-e-g-a.org/programming-basics-squared/)** (2018-06-12) — MEGA now offers the learning program “programming 1×1″ not only for elementary school students, but up to and including upper secondary/high school.
- **[Write with light](https://www.m-e-g-a.org/write-with-light/)** (2018-06-12) — “The Kaypro … let you write with light on glass, not ink on paper, which was mind-blowing.

### 2017 (3 posts)

- **[You should make a copy](https://www.m-e-g-a.org/you-should-make-a-copy/)** (2017-12-20) — For an upcoming exhibition we decided to use -amongst other machines- a Kaypro II “portable” computer from 1982 running CP/M 2.2.
- **[The Commodore Story](https://www.m-e-g-a.org/the-commodore-story/)** (2017-12-14) — Last weekend we were invited to London to the premiere of The Commodore Story by Steven Fletcher.
- **[Easter present](https://www.m-e-g-a.org/easter-present/)** (2017-04-23) — At Revision easter party (Demoscene event) in Saarbrücken/Germany we used the opportunity to work on the first MEGA65 mainboards Antti brought in his backpack.

### 2016 (5 posts)

- **[Analog to Digital](https://www.m-e-g-a.org/analog-to-digital/)** (2016-11-11) — For Rainald Grebe‘s Play “Anadigiding III” at Schauspiel Hannover, MEGA showed the transition from analog gaming, including the first analog video game and analog handheld games,…
- **[Very last AMIGA goes to: MEGA](https://www.m-e-g-a.org/the-very-last-amiga-goes-to-mega/)** (2016-04-08) — MEGA is fulfilling its mission of preserving mankind’s digital heritage at its best: The very last Amiga 1200 has been added to the MEGA collection!
- **[MEGA65 interview @ Scene World](https://www.m-e-g-a.org/mega65_scene_world/)** (2016-02-22) — Word is spread about the MEGA65 project on all channels!
- **[MEGA65 second prototype](https://www.m-e-g-a.org/mega-65-second-prototype/)** (2016-01-22) — Our mega project the MEGA65 open 8-bit computer reached the next milestone!
- **[Programming Basics: The Games](https://www.m-e-g-a.org/programming-basics-the-games/)** (2016-01-19) — Programming basics: Now that the winter lessons have ended, and all participants were rewarded, not only with the knowledge of how to program a computer, but also with a…

### 2015 (13 posts)

- **[Programming Basics: Winter 2015](https://www.m-e-g-a.org/programming-basics-winter-2015/)** (2015-11-17) — Programming Basics, our free course for fourth graders has started again: This time nine boys are learning how to program a computer.
- **[Lost Gems: Dark Castle (1986)](https://www.m-e-g-a.org/lost-gems-dark-castle-1986/)** (2015-11-16) — After receiving a generous donation from a Swiss fellow named “Louis” which -among other machines- included a boxed early Macintosh Plus we decided to play a bit with this Mac.
- **[MEGA65 first prototype](https://www.m-e-g-a.org/mega65-first-prototype/)** (2015-10-16) — At the AMIGA30 years event in Neuss, Germany, we showed the first MEGA65 prototype.
- **[Exhibition: Animated Wonderworlds](https://www.m-e-g-a.org/animated-wonderworlds/)** (2015-09-08) — The exhibition Animated Wonderworlds at Museum für Gestaltung Zurich is a wonderful modern trip through the facettes of animated images and electronic versatility.
- **[Trainee @ MEGA](https://www.m-e-g-a.org/trainee-mega-3/)** (2015-08-24) — Christina studies Creative Content Design at Mittweida university.
- **[Psychic Seeds](https://www.m-e-g-a.org/psychic-seeds/)** (2015-07-20) — 7 years after we reverse engineered the Nintendo Pokemon Mini micro game console and released the award winning SHizZLE demo there is still life in the PM scene!
- **[Programming Basics: Scratch the Snake](https://www.m-e-g-a.org/scratch-the-snake/)** (2015-05-18) — As part of the exhibition “Hamster Hipster Handy” we have reprogrammed the mobile game classic “Snake” in a workshop called “Scratch the Snake”.
- **[Hamster Hipster Handy vernissage](https://www.m-e-g-a.org/hamster-hipster-handy-vernissage/)** (2015-04-27) — The grand opening of the Hamster Hipster Handy exhibition at Museum Angewandte Kunst was a great event.
- **[MEGA65 8-bit computer](https://www.m-e-g-a.org/mega65-introduction/)** (2015-04-22) — MEGA65 is an open-source new and completely open C65-like computer.
- **[Hamster Hipster Handy Program](https://www.m-e-g-a.org/hamster-hipster-handy-program/)** (2015-03-31) — In addition to displaying exhibits MEGA will teach you how to program your first game: The mobile phone classic SNAKE.
- **[Exhibition: Hamster Hipster Handy](https://www.m-e-g-a.org/upcoming-hamster-hipster-handy/)** (2015-03-27) — April 25th – July 05th 2015, Museum Angewandte Kunst Frankfurt: Under the Spellbound of the Mobile Phone.
- **[DIY: TeleBall](https://www.m-e-g-a.org/diy-teleball/)** (2015-01-13) — TeleBall is an Arduino based “retro” handheld game console you can build by yourself.
- **[Lost Gems: Videoton TVC (1983)](https://www.m-e-g-a.org/lost-gems-videoton-tvc/)** (2015-01-12) — The rare and beautiful “TV Computer” was built by hungarian company Videoton in 1983.

### 2014 (19 posts)

- **[How to BANG!](https://www.m-e-g-a.org/how-to-bang/)** (2014-11-17) — Our friend Sv0lli from CCC explained at Hackover 2014 how he coded the Atari 2600 demo BANG!
- **[MEGA in Berlin](https://www.m-e-g-a.org/mega-in-berlin/)** (2014-11-14) — In the night from 12th to 13th November MEGA presented a unique exhibition for SAP at Berlin City Cube.
- **[Lost Gems: Ghost Manor (1984)](https://www.m-e-g-a.org/ghost-manor-1984/)** (2014-10-20) — An almost forgotten treasure has been dug out: Ghost Manor on the unexpanded Commodore VIC-20 computer is an action-packed arcade-style jump’n run game.
- **[Trainee @ MEGA](https://www.m-e-g-a.org/trainee-mega-2/)** (2014-10-14) — Felix wants to share his knowledge about the world in general and programming in particular.
- **[Day One@Programming Basics](https://www.m-e-g-a.org/programmingbasics_day1/)** (2014-10-01) — The first day of the Programming Basics study group at Joseph-Heckler-School Bensheim/Germany was a great success.
- **[Programming Basics](https://www.m-e-g-a.org/programmier1x1/)** (2014-09-23) — Programmier1x1 (programming basics) is a new venture of MEGA to provide children with no previous knowledge of basic concepts and methods of programming.
- **[Cassette Vision](https://www.m-e-g-a.org/cassette-vision/)** (2014-09-04) — Today we resurrected another obscure japanese game console: The Epoch Cassette Vision (カセットビジョン), not to be confused with the more popular Super Cassette Vision.
- **[Fake wood](https://www.m-e-g-a.org/fake-wood/)** (2014-08-18) — In the 1970s printed or fake wood was very popular for video game consoles.
- **[Trainee @ MEGA](https://www.m-e-g-a.org/trainee-mega/)** (2014-08-07) — Max studies Animation & Game at Darmstadt university.
- **[Hessian Day 2014](https://www.m-e-g-a.org/hessian-day-2014/)** (2014-06-08) — Hessian Day 2014 in Bensheim has begun.
- **[Addendum to the exhibition](https://www.m-e-g-a.org/addendum-to-the-exhibition/)** (2014-05-14) — The framework program to the MEGA exhibition NERDIFIED?
- **[NERDIFIED? summary](https://www.m-e-g-a.org/nerdified-summary/)** (2014-04-29) — After nine weeks on 21st of April 2014 the exhibition NERDIFIED?
- **[Atari 2600: Bang!](https://www.m-e-g-a.org/atari-2600-bang/)** (2014-04-27) — The Atari 2600 demo “Bang!”, coded by SvOlli of the Chaos Computer Club Hannover (Leitstelle 511) and co-produced by MEGA, was awarded first place at Revision Demoparty 2014 in…
- **[NERDIFIED? vernissage](https://www.m-e-g-a.org/nerdifierd-vernissage/)** (2014-02-23) — The exhibition opening of NERDIFIED?
- **[NERDIFIED? program](https://www.m-e-g-a.org/nerdified-program/)** (2014-02-18) — Exhibition opening Saturday, 22 February 2014 at 5 pm Museum Bensheim Entrance: Marktplatz 13 – 64625 Bensheim Navi: Platanenallee (Car Park, Exit Marktplatz) Keynote Nerds and…
- **[EBOOK HISTORY](https://www.m-e-g-a.org/ebook-history/)** (2014-02-04) — In 1990 SONY brought the first eBook reader to the market, the Data Discman.
- **[GAME&WATCH COLLECTORS CATALOG](https://www.m-e-g-a.org/gamewatch-collectors-catalog/)** (2014-01-27) — The culture of collecting in the field of computer and video games experiences a growing number of active people worldwide.
- **[Are you NERDIFIED?](https://www.m-e-g-a.org/are-you-nerdified/)** (2014-01-18) — On 22nd of February 2014 we launch the new special exhibition NERDIFIED?
- **[MEGA in Amsterdam](https://www.m-e-g-a.org/mega-in-amsterdam/)** (2014-01-08) — From 5th-7th November 2013 MEGA presented the exhibition “Game On.

### 2013 (24 posts)

- **[BIII Frankfurt summary](https://www.m-e-g-a.org/biii-summary/)** (2013-12-05) — On November 10th 2013 the exhibition EMERGENT <IMG> ended which was part of the “B3 Biennale des bewegten Bildes” parcours.
- **[Day Four @ MAK](https://www.m-e-g-a.org/day-four-mak/)** (2013-11-03) — Richard Garriott’s masterpiece, the role-playing game series “Ultima”, cornerstone of the genre, is displayed in a special exhibition.
- **[Day Three @ MAK](https://www.m-e-g-a.org/day-three-mak/)** (2013-11-02) — The second main course “Adventure” shows the history of computer based adventure games beginning with Zork, a text-only adventure from the early 1980s and playable on a classic…
- **[Day Two @ MAK](https://www.m-e-g-a.org/day-two-mak/)** (2013-11-01) — Thursday was a busy day at EMERGENT<IMG> / Museum Angewandte Kunst.
- **[Day One and Night@Museum](https://www.m-e-g-a.org/day-one-and-nightmuseum/)** (2013-10-31) — Wednesday was the first day of the the EMERGENT<IMG> exhibition at Museum Angewandte Kunst and the only chance to visit the exhibition at night besides today’s tour at 8:30 PM.
- **[Day Zero @ MAK](https://www.m-e-g-a.org/day-zero-mak/)** (2013-10-30) — All preparations for tomorrow’s grand opening are done.
- **[DEMOAGE MEGAontology](https://www.m-e-g-a.org/demoage-megaontology/)** (2013-10-21) — Canan Hastik presented DEMOAGE MEGAontology lightweight prototype @ Media Art Histories 2013 (MAH): Renew, 5th international conference on the Histories of Media Art, Science and…
- **[EMERGENT<IMG>](https://www.m-e-g-a.org/emergent/)** (2013-09-27) — For B3 Biennial of the moving image 2013 MEGA shows a tour of selected interactive exhibits displaying the development of figurative narrativity and ludic storytelling in…
- **[Day Four @ Ars Electronica](https://www.m-e-g-a.org/day-four-ars-electronica/)** (2013-09-09) — On this last exhibition day we present the fourth main focus of “Ludic Memento”.
- **[Day Three @ Ars Electronica](https://www.m-e-g-a.org/day-three-ars-electronica/)** (2013-09-08) — Another major focus in “Ludic Memento” is the juxtaposition of original home computers and emulators.
- **[Day Two @ Ars Electronica](https://www.m-e-g-a.org/day-two-ars-electronica/)** (2013-09-07) — One focus of “Ludic Memento” is dedicated to the Nintendo Game & Watch series.
- **[Day One @ Ars Electronica](https://www.m-e-g-a.org/day-one-ars-electronica/)** (2013-09-06) — Ludic Memento is an exhibition of this year’s festival focus on gaming.
- **[Day Zero @ Ars Electronica](https://www.m-e-g-a.org/day-zero-ars-electronica/)** (2013-09-04) — The exhibition concept “Ludic Memento” has been successfully set up by the MEGA team.
- **[MEGA outdoor exhibition](https://www.m-e-g-a.org/mega-outdoor-exhibition/)** (2013-07-17) — At the W&M summer festival numerous children of the many hundreds of visitors jumped into game worlds of the 80s.
- **[Trainees @ MEGA](https://www.m-e-g-a.org/trainees-mega/)** (2013-07-02) — Three trainees have joined MEGA to support our upcoming exhibitions.
- **[MEGA exposed](https://www.m-e-g-a.org/mega-exposed/)** (2013-07-02) — Do you want to get inside information about MEGA?
- **[FM Towns @ MEGA archive](https://www.m-e-g-a.org/fm-towns-mega-archive/)** (2013-06-05) — We are happy to add a super rare Fujitsu FM Towns to our archive.
- **[New PokeCard512](https://www.m-e-g-a.org/new-pokecard512/)** (2013-05-28) — A new version of the Pokemon Mini flash cartridge “PokeCard512″ is in the making.
- **[T42² @ Spielzeugmuseum Riehen](https://www.m-e-g-a.org/t42%c2%b2-spielzeugmuseum-riehen/)** (2013-05-20) — From May 25th Tennis for Two will be exhibited and playable in the special exhibition “Press Start to Play – experience video games” at toy museum Riehen (Switzerland) for seven…
- **[Wild compo @ Revision 2013](https://www.m-e-g-a.org/wild-compo-revision-2013/)** (2013-05-20) — As part of the “Wild Competition” at this year’s Revision Easter Party, world’s most important demoscene event, “Code Red” by MEGA reached second place.
- **[MEGA @ Revision 2013](https://www.m-e-g-a.org/mega-revision-2013/)** (2013-03-29) — Demoscene Exposed: Micro And Macro Ways Through The Maze.
- **[MEGA @ CEBIT 2013](https://www.m-e-g-a.org/mega-cebit-2013/)** (2013-03-18) — Similar to SAPPHIRE NOW in Madrid at the SAP booth at CeBIT / Hall 4 from 5th to 9th of March 2013 the “History Wall: 40 Years of Inspiration” was presented featuring exhibits…
- **[Media archaeological power workout](https://www.m-e-g-a.org/media-archaeological-power-workout/)** (2013-01-23) — New shizzle from MEGA?
- **[MEGA @ Biennial BIII](https://www.m-e-g-a.org/mega-biennial-biii/)** (2013-01-09) — The new B3 Biennial was presented for the first time to the public in a one-day event.

### 2012 (8 posts)

- **[MEGA supports SAP with exhibits](https://www.m-e-g-a.org/mega-supports-sap-with-exhibits/)** (2012-12-05) — In 2011 MEGA already matched milestones of the history of technology with the evolution of SAP in the exhibiton “Digital Revolution”.
- **[MEGA exhibiting on holy ground](https://www.m-e-g-a.org/mega-exhibiting-on-holy-ground/)** (2012-11-23) — An ancient church has been the exhibition space for the “LOOK & FEEL” exhibition.
- **[All roads lead to Rome](https://www.m-e-g-a.org/all-roads-lead-to-rome/)** (2012-11-02) — The opening of VIGAMUS – Video Game Museum of Rome was a great success!
- **[MEGA and VIGAMUS sign cooperation contract](https://www.m-e-g-a.org/mega-and-vigamus-sign-cooperation-contract/)** (2012-09-26) — A cooperation of MEGA – Museum of Electronic Games & Art – and ViGaMus – Video Game Museum of Rome, has been started.
- **[Tennis For Two with New Media @ gamescom 2012](https://www.m-e-g-a.org/tennis-for-two-with-new-media-gamescom-2012/)** (2012-08-30) — Numerous interested vistors experienced Tennis For Two with New Media at gamescom 2012 in Cologne and were impressed by fun gameplay as well as the fascination for the history of…
- **[MEGA @ gamescom 2012](https://www.m-e-g-a.org/mega-gamescom-2012/)** (2012-08-08) — Visit us at gamescom 2012!
- **[MEGA @ Nat Geo’s New Documentary Series “The Link”](https://www.m-e-g-a.org/t42national-geographics-new-documentary-series-links/)** (2012-06-02) — MEGA @ Nat Geo’s New Documentary Series “The Link” History’s Greatest Tech.
- **[MEGA calendar 2012](https://www.m-e-g-a.org/mega-calendar-2012/)** (2012-02-01) — Trying hard to finish the new calendar 2012!

### 2011 (8 posts)

- **[Tennis for Two App](https://www.m-e-g-a.org/tennis-for-two-app/)** (2011-12-17) — Check this out: Discover the most important object in the history of electronic gaming: Play a simulation of the famous T42 – Tennis for Two by MEGA – Museum of Electronic Games &…
- **[MEGA @ PlayStation.Blog](https://www.m-e-g-a.org/mega-playstation-blog/)** (2011-09-19) — The Museum of Electronic Games & Art is dedicated to the task of thoroughly analyzing the history of our passion and presenting it in detailed renovations.
- **[T42 (Tennis for Two) @ gamescom 2011](https://www.m-e-g-a.org/t42-tennis-for-two-gamescom-2011/)** (2011-08-24) — People enjoying T42 – Tennis for Two – at gamescom 2011.
- **[Coming up Soon! RETURN-The 8-Bit magazine](https://www.m-e-g-a.org/return-coming-up-soon/)** (2011-07-06) — Coming up soon!
- **[MEGA @ Mediale* 2011](https://www.m-e-g-a.org/mega-mediale-2011/)** (2011-06-13) — 1 2 ►
- **[MEGA @ SAP DKOM 2011](https://www.m-e-g-a.org/mega-sap-dkom-2011/)** (2011-06-13) — DIGITAL REVOLUTION March 15, 2011 at SAP DKOM in Mannheim (SAP Arena, Trainingshalle) An exhibition about revolutionary inventions and life in a digital world.
- **[MEGA @ Revision 2011](https://www.m-e-g-a.org/mega-revision-2011/)** (2011-06-13) — On 22nd to 25th of April 2011 at Revision demoparty in Saarbrücken, Germany, MEGA had an entry in the “Wild Competition” showing the making-of-video of our Tennis for Two replica…
- **[MEGA @ Assembly 2010](https://www.m-e-g-a.org/mega-assembly-2010/)** (2011-06-13) — 1 2 3 ►

### 2010 (1 post)

- **[There is an app for everything](https://www.m-e-g-a.org/there-is-an-app-for-everything/)** (2010-08-26) — Unique Lifestyle app that will bring back your childhood memories and tears to your eyes!
