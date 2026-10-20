# ARHoops

A mobile AR basketball game built with Unity and AR Foundation. Scan your floor, place a hoop anywhere in your room, and swipe to shoot. Walk closer or farther away and the game adapts: longer shots are worth more points and need a more precise swipe.

> 🎥 **Demo video coming soon.**

## Download and Play

Grab the latest APK from the [Releases](../../releases) page and install it on an [ARCore-supported Android device](https://developers.google.com/ar/devices).

1. Download `ARHoops.apk` on your phone.
2. Open it and allow installing from this source when asked.
3. Launch ARHoops, allow camera access, and point your phone at the floor.

## Features

### Gameplay
- Two modes: **Free Shoot** (no score, no timer) and **30 Sec Challenge**
- Distance-based scoring: 1, 2 or 3 points depending on how far you shoot from
- Shot trajectory solved with projectile motion, with a sweet spot that tightens with distance
- Accurate basket detection: only balls that drop through the rim from above count
- Best score saved on device

### AR
- Floor detection with ARCore plane tracking
- Tap to place the hoop on your real floor, facing you
- Hoop can be moved between rounds, and is locked during a challenge
- Plane overlay hides once the hoop is placed, so you just see your room

### Feedback and UI
- Swish, rim, backboard and floor sounds, with volume based on impact speed
- Particle burst on every basket
- Colour-coded +1 / +2 / +3 popups at the rim
- Final 5-second centre countdown
- Step-by-step on-screen hints (scan, place, pick a mode, shoot)

## How It Works

**Placing the hoop.** Screen taps are raycast against ARCore's detected planes, and the hoop is placed at the hit point, turned to face the player. Taps and swipes are told apart by finger movement, and button presses are filtered out so they never move the hoop.

**Shooting.** For each shot, the game measures the distance to the rim and solves the projectile equations for a throw that peaks above the rim and drops through its centre, with higher arcs for longer shots. The swipe length is compared to an ideal swipe for that distance. Inside the sweet spot, the ball follows the solved path; outside it, the ball falls short or overshoots. The sweet spot narrows with distance, so 3-pointers are harder.

**Scoring.** A trigger zone tracks each ball's centre around the rim. A basket counts only if the ball enters from above inside the scoring circle and drops below the rim while still inside and falling. Bounce-outs, air balls and balls coming up from below don't count.

**Game flow.** A small state machine (waiting for hoop, menu, challenge, free shoot, game over) controls the UI, shooting, scoring and whether the hoop can be moved.

## Controls

| Action | How |
|---|---|
| Place or move the hoop | Tap the floor |
| Shoot | Swipe up (longer swipe = stronger throw) |
| Aim left or right | Angle the swipe left or right |

## Tech Stack

- Unity 6
- AR Foundation + Google ARCore XR Plugin
- C#
- Unity Input System
- TextMeshPro
- Blender

## Source Code

The source code is kept private. It's available on request for recruiters and interviewers.

## Credits

- Basketball hoop model from [Poly Pizza](https://poly.pizza)
- Sound effects from free sound effect libraries

---

© 2026 Sharanya C Bharadwaj. All rights reserved.
