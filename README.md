# How to Play Asteroids

## Overview

You pilot a lone spacecraft stranded in an asteroid field. Destroy every asteroid to advance to the next level — but watch out for the UFO that occasionally swoops in to hunt you down. Survive as long as possible and chase the high score.

---

## Starting the Game

Open `index.html` in your browser and press **Enter** to begin. The same key restarts the game after a Game Over.

---

## Controls

| Key | Action |
|-----|--------|
| `←` `→` | Rotate the ship left / right |
| `↑` | Thrust forward |
| `Space` | Fire (hold for automatic fire) |
| `H` | Hyperspace — emergency teleport |
| `S` | Activate shield |
| `P` or `Esc` | Pause / unpause |
| `Enter` | Start or restart |

### Mobile

Touch controls appear automatically on touch-screen devices — buttons for rotate, thrust, fire, hyperspace, and shield are displayed at the bottom of the screen.

---

## The Basics

### Movement

Your ship moves with **inertia** — just like in space. Tapping thrust adds speed in the direction you are pointing, but the ship will keep drifting until friction gradually slows it down. Plan your turns ahead of time.

The screen **wraps**: flying off one edge brings you out the opposite side, and the same applies to asteroids and bullets.

### Shooting

Press or hold **Space** to fire bullets. You can have a maximum of **6 bullets** on screen at once. Bullets also inherit a portion of your ship's velocity, so shooting while moving gives them a boost.

---

## Asteroids

Asteroids come in three sizes. Shooting one breaks it apart:

| Size | Points | What happens when shot |
|------|--------|------------------------|
| Large | 20 | Splits into 2 medium asteroids |
| Medium | 50 | Splits into 2 small asteroids |
| Small | 100 | Destroyed completely |

Clear every asteroid on screen to advance to the next level.

> **Tip:** Newly spawned fragments fly outward at higher speed than the original — stay mobile after breaking a large asteroid.

---

## The UFO

A UFO periodically crosses the screen and opens fire. There are two variants:

| Type | Colour | Behaviour |
|------|--------|-----------|
| Large UFO | Green | Fires in random directions |
| Small UFO | Green | **Aims directly at your ship** |

Shooting the UFO scores **200 points**. If you ignore it, it will fly off the screen after a while and eventually return.

---

## Special Abilities

### Shield (`S`)

Activating the shield surrounds your ship with a protective field for a few seconds.

- Incoming asteroids are **deflected** (they bounce back).
- UFO bullets are **absorbed**.
- The shield has a cooldown after each use.

### Hyperspace (`H`)

Instantly teleports your ship to a random location on screen. Use it to escape a hopeless situation. The landing spot is random, so you may end up in danger — use it as a last resort.

---

## Lives & Scoring

- You start with **3 lives**.
- Every **10,000 points** you earn a bonus ship (up to a maximum of 6).
- When all lives are lost the game ends and your final score is shown.
- Your **high score** is saved locally in the browser and persists between sessions.

### Point Values at a Glance

| Target | Points |
|--------|--------|
| Large asteroid | 20 |
| Medium asteroid | 50 |
| Small asteroid | 100 |
| UFO | 200 |

---

## Tips & Strategy

- **Don't sit still.** A stationary ship is an easy target for both asteroids and the UFO.
- **Clear from the edges in.** Shoot large asteroids near the edge of the screen so the fragments have room to spread without crowding you.
- **Listen to the beat.** The background pulse speeds up as the asteroid count drops — a fast beat means you are nearly done with the level.
- **Save the shield for emergencies.** It has a cooldown, so don't waste it on a near-miss.
- **Respect the small UFO.** It leads its shots, so erratic movement is your best defence.
- **Watch for wrap-around ambushes.** An asteroid or UFO bullet that exits one side of the screen reappears on the opposite side immediately.

---

## Levels

Each new level adds more asteroids, making the field progressively more crowded. UFO visits also become more frequent as levels rise. There is no final level — survive as long as you can.

---

*Good luck, pilot.*
