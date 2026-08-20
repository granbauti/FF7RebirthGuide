# Changelog

All notable public releases of FF7 Rebirth Completion Guide Overlay.

## v0.8.0 — smarter routing, chapter detection, search and trust

Supported game build: Steam 23447986 (PC 1.005), unchanged.

- **Search.** Type-to-filter box above the checklist: find anything by name,
  hint, region or category across the whole game at once (anti-spoiler still
  applies — unreached regions never surface in results).
- **Completion Audit.** One click lists everything still missing game-wide,
  grouped by region with its unlock state, with a copy-to-clipboard report.
- **Anti-spoiler now lifts as you progress.** Reaching a region reveals its
  names automatically; only regions ahead of your story stay masked.
- **The overlay teaches itself.** The welcome text-wall is gone — short
  one-time tips appear the first time each key matters (marker, panel
  interaction, menu pinning). The checklist now opens on the "Current" view.
- **Quality of life.** The overlay closes itself when the game closes; the
  main menu shows a quiet "no save loaded" state instead of a fake fresh-run
  checklist; per-category progress moved into the section headers (the old
  overflowing ring strip is gone); "Check for updates" button in Settings
  (opens your browser — the overlay itself still never touches the network).
- **Trust.** The zip now ships `QUICKSTART.txt` and `TRUST.md` — an
  append-only release hash history plus instructions to verify the
  read-only / no-network claims yourself with standard tools.
- More accurate unlock chapters for ~150 activities (audited game-wide), and
  pursuing a target that has no map anchor now says so instead of leaving
  the marker on the previous target.

- **Nearest-station routing.** Actions you can do at any of several places —
  Chadley's combat simulator, the six world pianos, delivering photos to
  Snaps — now point the marker at the nearest station inside your current
  region instead of one fixed spot. Walk up to the Chadley in front of you,
  not the one a kilometre away.
- **Chapter detection fixed.** The header chapter now updates the moment a
  new chapter starts (it previously lagged at chapter transitions), and it
  follows the chapter of whatever save you are actually playing.
- **Loading a different save mid-session fixed.** Switching saves from the
  in-game Load menu no longer leaves the overlay showing the previous
  save's region, a stuck "over the game's menu" indicator, or markers
  pointing at far-away stations. The overlay now detects the switch and
  re-syncs itself within a few seconds — no restart needed.

## v0.7.0-rc2 — first public release

Supported game build: Steam 23447986 (PC 1.005).

- Live completion tracking for the whole game: quests (with per-step
  waypoints), treasure, World Intel including phenomenon/protorelic chains,
  Queen's Blood, Chadley's VR challenges, minigames and their stage/course
  progressions, Johnny collectibles and trophy cards.
- 3D world markers with distance, action hints and automatic advance as
  the game registers progress.
- Goal pursuit ("chase"): pick any target and the overlay walks its unlock
  chain to whatever you can act on right now, telling you when a goal is
  blocked and by what.
- Guide modes (Completionist / Essentials / Platinum), anti-spoiler mode,
  fast-travel suggestions, rebindable hotkeys, postponable checklist items.
- Read-only by design: no memory writes, no injection, no file
  modification, no network. Fail-closed on unsupported game builds.
