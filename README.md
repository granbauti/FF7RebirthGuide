# FF7 Rebirth Completion Guide Overlay

A **read-only** companion overlay for FINAL FANTASY VII REBIRTH (PC, Steam) that
tracks your 100% / platinum progress live while you play.

![status](https://img.shields.io/badge/game%20build-Steam%2023447986%20(PC%201.005)-blue)

## What it does

- **Live completion tracking** — quests, treasure chests, World Intel
  (towers, fiend sightings, lifesprings, phenomenon/protorelic chains,
  divine intel, excavations, moogles), Queen's Blood, Chadley's VR
  challenges, minigames, Johnny's Seaside Inn collectibles and trophy cards.
- **3D ESP markers** — an in-world marker guides you to the nearest
  incomplete activity, with distance, action hints and quest-step tracking
  that advances the moment the game registers your progress.
- **Dependency-aware guidance** — every activity knows what unlocks it.
  "Chase" any goal (a trophy card, a VR challenge, a quest) and the overlay
  walks its prerequisite chain down to the thing you can actually do right now.
- **Anti-spoiler mode** (on by default) — future region and chapter names
  stay hidden until you reach them.
- **Guide modes** — Completionist, Essentials and Platinum presets, chosen
  in a first-run welcome wizard.

## How it works (and what it never does)

The overlay attaches to the running game with **query and read-only memory
rights**. It never writes to game memory, never injects code or DLLs, never
modifies game files or saves, and never touches the network. If the game
build does not exactly match the supported fingerprint, the overlay refuses
to attach (fail-closed) rather than guess.

Supported build: **Steam build 23447986 (PC version 1.005)**. Other builds
are rejected on purpose.

## Compatibility

- **CPU**: any 64-bit Intel or AMD processor (no special instruction sets
  required).
- **GPU**: anything with DirectX 11 support — NVIDIA, AMD or Intel
  integrated graphics all work. The overlay is lightweight.
- **OS**: Windows 10 or 11, 64-bit.
- **Dependencies**: none. Single self-contained executable — no Visual C++
  redistributable, no installer.
- **Display mode**: run the game in **Borderless** (or Windowed) mode so
  the overlay can draw on top. In exclusive Fullscreen the overlay may not
  be visible.

## Usage

1. Start FINAL FANTASY VII REBIRTH (Borderless recommended).
2. Run `FF7RebirthGuide.exe`. It finds the running game automatically —
   you can also start the overlay first; it waits for the game.
3. On first run a small wizard lets you pick a guide mode.
4. Play.

### Hotkeys (all rebindable in Settings)

| Key | Action |
|---|---|
| **F7** | Toggle the 3D ESP markers |
| **F8** | Toggle **mouse interaction** — enables the cursor so you can click, scroll and drag inside the overlay panels; press again to give control back to the game |
| **F9** | Hide / show the overlay |
| **F10** | Switch between the compact widget and the expanded panel |
| **End** | Quit the overlay |

Tip: the overlay is click-through by default so it never steals your game
input. Press **F8** whenever you want to use the menus (change settings,
rebind keys, postpone items, press "chase" buttons), and **F8** again to
return control to the game.

### Files it creates

The overlay saves your settings, window layout and postponed-items list as
small `.ini` files **next to the executable**. Put the exe in its own
normal folder (Documents, Desktop, D:\Tools\... — anywhere you can write;
avoid `C:\Program Files`, where Windows blocks the settings files).
Uninstalling = deleting the folder; nothing is written to the registry or
anywhere else.

## Verify your download

Each release publishes the SHA-256 of the executable in its release notes.

```
certutil -hashfile FF7RebirthGuide.exe SHA256
```

## Troubleshooting

- **Windows SmartScreen warns about an unknown publisher** — expected for
  an unsigned community tool. Verify the SHA-256 against the release notes,
  then "More info > Run anyway".
- **Antivirus flags it** — the overlay reads the memory of a running game,
  which some heuristics dislike. It performs no writes and no injection;
  verify the hash and whitelist it if you trust the release.
- **"Waiting for FINAL FANTASY VII REBIRTH to start..." never ends** —
  make sure the game is actually running. If it is and you launched Steam
  as administrator, run the overlay as administrator too. A custom install
  location can always be passed explicitly:
  `FF7RebirthGuide.exe --target "D:\...\ff7rebirth_.exe"`
- **"Unsupported build" error** — your game version differs from Steam
  build 23447986 (PC 1.005). The overlay refuses to guess on unknown
  builds; wait for a release that supports your version.
- **Overlay not visible in-game** — switch the game to Borderless display
  mode.

## Fair play note

This is an informational overlay only: it reads your own progress and draws
on your own screen. It grants no gameplay advantage the in-game menus do not
already provide. Use at your own discretion; it is not affiliated with or
endorsed by Square Enix.

## Reporting issues & contributing

**Bug reports and suggestions are very welcome — please open a GitHub
issue** with: your game build (Steam > Properties > Updates), what you
expected, what the overlay showed, and a screenshot if possible.

**Pull requests are not accepted.** This project distributes binary
releases only (the source is not published), so there is nothing a PR can
change — any PRs opened will be closed. Issues are the right channel for
everything.
