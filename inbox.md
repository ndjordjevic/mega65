# Inbox

Drop URLs below under `## Pending`. Run `/pin-llm-wiki run <url>` to ingest a single URL (auto-queues it if missing), or `/pin-llm-wiki run` to batch-process every pending item. Agents may use `/pin-llm-wiki queue <url>` to suggest URLs without immediately ingesting them.

## Pending

<!-- Add URLs here, one per line, as markdown checkboxes.
     Supported inline tags (append each wrapped in HTML comment syntax):
       detail:brief        — override detail level for this source
       detail:standard
       detail:deep
       branch:dev          — GitHub: use this branch instead of default
       clone               — GitHub deep: full git clone to raw/github/<org>-<repo>/
       skip                — skip this URL on the next run
       companion:github.com/<org>/<repo>  — web: use this repo as companion (skip auto-discovery)
       no-companion        — web: suppress companion GitHub fetch even if a repo is found
       note: <text>        — freeform note for human review (ignored by ingest)
-->

<!-- Websites -->

<!-- GitHub repos -->

<!-- YouTube: playlists are not ingestible — expand first, then queue picked videos here.
     yt-dlp --flat-playlist --print "https://www.youtube.com/watch?v=%(id)s  # %(title)s" "https://www.youtube.com/playlist?list=PLPehmjqZolWArdt53pl1QyJurZDu3oJKy"
     yt-dlp --flat-playlist --print "https://www.youtube.com/watch?v=%(id)s  # %(title)s" "https://www.youtube.com/playlist?list=PLRVBh2hjFTomDGwIT7uPMJv4zH9JAUSVG"
-->

## Completed

- [x] https://mega65.org/ <!-- detail:deep --> <!-- note: official site; companion discovery of mega65-core is desirable --> <!-- ingested 2026-06-10 -->
- [x] https://dansanderson.com/mega65/ <!-- detail:deep --> <!-- no-companion --> <!-- note: hub site; deep crawl must include /mega65/welcome/ (the Welcome Guide, best beginner doc) plus Digest and cross-dev series --> <!-- ingested 2026-06-10 -->
- [x] https://retrocombs.com/mega65 <!-- note: resource page + User's Guide chapter walkthroughs --> <!-- ingested 2026-06-10 -->
- [x] https://retrocogs.mega65.com/ <!-- note: 45GS02/VIC-IV coding tutorials blog --> <!-- ingested 2026-06-10 -->
- [x] https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/ <!-- note: cross-dev setup guide --> <!-- ingested 2026-06-10 -->
- [x] https://files.mega65.org/html/main.php <!-- detail:brief --> <!-- no-companion --> <!-- note: filehost; catalog only --> <!-- ingested 2026-06-10 -->
- [x] https://mega65.atlassian.net/wiki/spaces/MEGA65/overview <!-- detail:standard --> <!-- note: full page index via REST API; 9 sections, 66+ pages catalogued --> <!-- ingested 2026-06-10 --> <!-- refreshed 2026-06-12 -->
- [x] https://www.c64-wiki.com/wiki/mega65 <!-- detail:brief --> <!-- note: background/history reference --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/MEGA65/mega65-user-guide <!-- detail:deep --> <!-- clone --> <!-- note: LaTeX source of all 5 official books; the greppable spec --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/RetroCogs/Mega65Tutorials <!-- detail:standard --> <!-- clone --> <!-- note: 45GS02 assembly tutorials with code --> <!-- ingested 2026-06-10 --> <!-- refreshed 2026-06-12 -->
- [x] https://github.com/MEGA65/mega65-tools <!-- note: mega65_ftp, etherload, CLI dev tools --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/MEGA65/mega65-code-snippets <!-- note: meta-repo of example code --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/dansanderson/easyasm65 <!-- note: on-device assembler --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/lgblgblgb/xemu <!-- detail:brief --> <!-- note: emulator; usage docs only, skip internals --> <!-- ingested 2026-06-10 -->
- [x] https://github.com/MEGA65/mega65-core <!-- detail:brief --> <!-- note: FPGA core; brief until hardware-level questions arise --> <!-- ingested 2026-06-10 -->

<!-- Processed lines are moved here automatically.
     Format after ingest: - [x] https://... with an "ingested YYYY-MM-DD" HTML comment appended.
     To re-fetch: add a "refresh" HTML comment to the line, then run /pin-llm-wiki run.
     The refresh tag is removed automatically after re-fetch.
-->
