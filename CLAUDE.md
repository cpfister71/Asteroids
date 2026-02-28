# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the Game

Open `index.html` directly in a browser — no build step, no server, no dependencies. All HTML, CSS, and JS live in that single file.

## Code Structure

Everything is inside one IIFE at the bottom of `index.html`. Sections are separated by banner comments (e.g., `// ─── SHIP ───`), in this order:

| Section | Description |
|---|---|
| CANVAS SETUP | Responsive canvas sizing; `W()` / `H()` getters |
| AUDIO | Web Audio API — procedural sounds only, no audio files. `ensureAudio()` must be called before any sound (browser policy) |
| HELPERS | `wrap()` (screen wrapping), `dist()`, `rnd()` |
| CONSTANTS | All tunable game values (`SHIP_SIZE`, `BULLET_SPEED`, `ASTEROID_RADII/SPEEDS/VERTS`, `SCORES`, etc.) |
| STATE | Top-level mutable state: `gameState`, `score`, `lives`, `ship`, `asteroids`, `bullets`, `particles`, `ufo`, `ufoBullets`, `keys` |
| DOM | HUD updates (`updateHUD`) and temporary message display (`showMessage`) |
| SHIP | `createShip()`, `drawShip()` — ship is a plain object, not a class |
| ASTEROIDS | `createAsteroid(x, y, size)`, `spawnAsteroids()`, `drawAsteroid()` |
| BULLETS | `fireBullet()` — shared by ship (`bullets[]`) and UFO (`ufoBullets[]`) via `fromShip` flag |
| UFO | `spawnUFO()`, `updateUFO()`, `drawUFO()` — timer-based spawning every `UFO_INTERVAL` frames |
| PARTICLES | Simple particle pool with fade-out |
| GAME LIFECYCLE | `startGame()`, `nextLevel()`, `killShip()`, `respawnShip()`, `gameOver()` |
| SCORE / BONUS LIVES | `addScore()` — handles extra-life threshold and high score in `localStorage` |
| CONTROLS | Keyboard events + mobile touch buttons (auto-added when `ontouchstart` detected) |
| MAIN LOOP | `loop(now)` via `requestAnimationFrame` — updates then draws; `dt` normalized to 60 fps |
| STARFIELD | 120 static stars stored as fractional coordinates, scaled to canvas on draw |

## Game Loop Flow

Each frame in `loop()`:
1. Clear canvas
2. If not `playing`/`paused`, draw stars and return early
3. Compute `dt` (frame-time ratio, clamped to 3× to avoid spiral-of-death)
4. Update: ship physics → bullets → asteroids → UFO → collisions → beat tempo → level check
5. Draw: particles → dim stars → asteroids → UFO → bullets → ship

## Key Design Patterns

- **Screen wrap**: all entities use `wrap(val, max)` on both axes each frame.
- **Collision detection**: simple radius checks (`dist(a, b) < r1 + r2`); asteroid hit uses `r * 0.75` to feel fair.
- **Shield**: `ship.shieldTimer > 0` deflects asteroids (reverses velocity) and absorbs UFO bullets instead of killing the ship.
- **Beat system**: `beatInterval` shrinks as `asteroids.length` drops; alternating low tones at 80 Hz / 60 Hz.
- **Audio laziness**: `ac` (AudioContext) is `null` until first user interaction to comply with autoplay policy.
- **High score**: persisted via `localStorage.getItem/setItem('asteroidsHigh')`.
