# 🍔 Burger Stack!

**A one-tap burger-stacking arcade game built for YouTube Playables.**

Ingredients slide across the screen — tap at the perfect moment to drop them on your burger. Miss the mark and the overhang gets sliced off, making your burger skinnier. Nail a **PERFECT** drop and your burger grows back wider while your combo (and cash) multiplies. How tall can you build before your burger topples?

🎮 **Play it:** `https://tamilninja.github.io/burgerstack/`

![Genre](https://img.shields.io/badge/genre-hyper--casual-orange)
![Platform](https://img.shields.io/badge/platform-YouTube%20Playables%20%7C%20Web-red)
![Size](https://img.shields.io/badge/size-22%20KB-brightgreen)
![Dependencies](https://img.shields.io/badge/dependencies-zero-blue)

---

## How to Play

| Action | Control |
|---|---|
| Drop ingredient | **Tap** (mobile) / **Click** or **Space** (desktop) |
| Restart | Tap after "ORDER UP!" |

- 🎯 **Perfect drop** (near-exact alignment) → combo goes up, burger regrows wider, cash multiplies
- 🔪 **Off-center drop** → the overhang is sliced off and your burger gets narrower
- 💥 **Total miss** → ORDER UP! Your score is the number of layers stacked
- 💰 Every layer earns cash — combos multiply your earnings

## Features

- 🍅 6 ingredients that cycle as you climb: patty, cheese, lettuce, tomato, onion, bacon
- ⚡ Speed ramps up the higher you stack
- 🌅 Background shifts from daytime blue to sunset as your tower grows
- ✨ Full arcade juice: screen shake, particle bursts, floating combo text, rising-pitch perfect dings
- 🏆 Best score and total cash saved between sessions
- 📱 Fully responsive — portrait, landscape, mobile, and desktop

## Tech

- **One file.** The entire game is `index.html` (~22 KB) — game loop, physics, rendering, and UI.
- **Zero assets.** All graphics are drawn with Canvas 2D; all sound effects are synthesized live with WebAudio. No images, fonts, or audio files — and no external network requests (a YouTube Playables requirement).
- **No frameworks.** Vanilla JavaScript, no build step, no dependencies.

## YouTube Playables SDK Integration

The game loads the official SDK (`https://www.youtube.com/game_api/v1`) and implements the full integration contract:

| SDK API | Used for |
|---|---|
| `game.firstFrameReady()` / `game.gameReady()` | Load lifecycle signals |
| `engagement.sendScore({ value })` | Submitting your score at game over |
| `game.saveData()` / `game.loadData()` | Persisting best score and cash |
| `system.isAudioEnabled()` / `onAudioEnabledChange` | Respecting YouTube's mute toggle |
| `system.onPause()` / `onResume()` | Pausing when YouTube pauses the game |

Outside the Playables environment everything gracefully falls back (saves go to `localStorage`), so the game runs perfectly in any normal browser too.

## Run Locally

```bash
npx http-server -p 4173 .
# open http://localhost:4173
```

Or just double-click `index.html`.
