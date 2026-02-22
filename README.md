# REFLEX — Reaction Timer

A fast, visually immersive browser-based reaction timer game built with vanilla JavaScript and Three.js. Designed as a portfolio project demonstrating precise timing mechanics, WebGL visuals, and polished UI.

![REFLEX Reaction Timer](https://img.shields.io/badge/version-1.0-blue) ![License](https://img.shields.io/badge/license-MIT-green) ![Vanilla JS](https://img.shields.io/badge/built%20with-Vanilla%20JS-yellow)

---

## Demo

Open `index.html` in any modern browser — no build step, no install, no dependencies beyond a CDN connection.

---

## Features

- **Three.js 3D scene** — an animated icosahedron reacts to game state in real time, shifting color, rotation speed, and emissive glow based on what's happening in the game
- **Precise millisecond timing** — uses `performance.now()` for sub-millisecond accuracy
- **Randomized stimulus delay** — between 1 and 5 seconds, preventing anticipation patterns
- **False start detection** — clicking before the signal triggers a penalty and logs a DNF
- **Session statistics** — tracks average, best, last, and total attempt count across the session
- **Round history** — every attempt is logged with a badge (BEST / OK / FALSE), newest first
- **Performance rating** — results are graded from Amazing (< 150ms) to Below Average (> 400ms)
- **Responsive layout** — works on desktop and mobile, with touch event support
- **Keyboard support** — Space bar triggers reactions in addition to click/tap

---

## How to Play

1. Click **START** or press **Space** to begin a round
2. Watch the 3D shape — wait for it to turn **green** and display **GO!**
3. Click anywhere in the arena (or press Space) as fast as you can
4. Your reaction time appears in milliseconds
5. The next round starts automatically after 2 seconds
6. Click **RESET** at any time to clear the session and start fresh

---

## Game States

| State | Shape Behavior | Color |
|-------|----------------|-------|
| Idle | Slow rotation | Neutral dark |
| Waiting | Amber pulse | Amber wireframe |
| Ready (GO!) | Fast pulse + glow | Green emissive |
| Result | Explosion scale burst | Blue emissive |
| False Start | Fast spin | Red emissive |

---

## Tech Stack

- **HTML/CSS/JavaScript** — no frameworks, no build tools
- **Three.js r128** — loaded via CDN for 3D rendering
- **Google Fonts** — Outfit (UI) and JetBrains Mono (timer/stats)
- **`performance.now()`** — high-resolution timing API

---

## Project Structure

```

reaction-game
├── index.html  # Main game file
├── README.md   # This file 
└── favicon.png # Game icon (optional)
```

The entire project is a single self-contained `index.html` file.

---

## Score Guide

| Rating | Time |
|--------|------|
| 🏆 Amazing | < 150 ms |
| ⚡ Very Good | 150 – 200 ms |
| 🎯 Good | 200 – 300 ms |
| ✓ Average | 300 – 400 ms |
| 📉 Below Average | > 400 ms |

Average human reaction time is approximately 200–250ms. Elite athletes can approach 150ms.

---

## Design Decisions

**Single file architecture** — keeping everything in one HTML file makes the project trivially portable and easy to share or review without a dev environment.

**Three.js as state feedback** — rather than treating the 3D scene as pure decoration, the shape's color, speed, and scale are driven by game state. This makes the visual layer functional, not cosmetic.

**No framework dependency** — vanilla JS keeps the timing logic transparent and avoids abstraction layers that could introduce latency or obscure how the game actually works.

**`performance.now()` over `Date.now()`** — provides sub-millisecond resolution and is not subject to system clock adjustments, making it the correct tool for timing games.

**Automatic round progression** — rounds advance automatically after a short delay so the user stays in flow rather than having to manually trigger each new round.

---

## Browser Support

Works in all modern browsers supporting WebGL and ES6+. Tested in Chrome, Firefox, Safari, and Edge.

---
