# Rock · Paper · Scissors — Hand-Sign Showdown

A single-file, no-dependency Rock Paper Scissors game — with two extra game modes thrown in — built in plain HTML, CSS, and JavaScript. Play against the computer, watch an animated "shake and reveal," and keep score across sessions.

Deployment URL : https://rock-paper-scissors-sage-two.vercel.app/

---

## Demo Video

https://drive.google.com/file/d/1t2X5M81dtIZsxS9qTXz9m43A5Q5_wf1C/view?usp=sharing

---

## Features

- **Three game modes**, switchable with a tab bar — each with its own color identity and win/lose logic:
  - 🪨 **Rock, Paper & Scissors** — the classic
  - 💃 **Lady, Hunter & Tiger** — a popular schoolyard variant
  - 🐍 **Snake, Water & Gun** — another regional variant
- **Animated reveal** — a "Rock… Paper… Scissors… Shoot!" style countdown plays before both hands are revealed at the same time, so it feels like an actual showdown instead of an instant result.
- **Live scoreboard** — tracks wins, losses, ties, and rounds played, tracked **separately per mode** so switching tabs doesn't erase your progress in the others.
- **Confetti burst** on every win.
- **Reset button** to clear the score for whichever mode you're currently playing.
- **Accessible by default** — visible keyboard focus states, `prefers-reduced-motion` support, and semantic tab roles.
- **Fully responsive** — works on mobile, tablet, and desktop.

---

## How to play

1. Open `rock-paper-scissors.html` in a browser.
2. Pick a game mode from the tab bar at the top (Rock Paper Scissors is selected by default).
3. Click one of the three move buttons.
4. Watch the countdown, then see who wins the round.
5. Scores update automatically. Click **Reset scores for this game** to start over.

---

## Game modes & rules

Each mode is a closed loop of three moves — every move beats exactly one other and loses to exactly one other.

### 🪨 Rock, Paper & Scissors
| Move | Beats |
|------|-------|
| Rock | Scissors (smashes) |
| Paper | Rock (covers) |
| Scissors | Paper (cuts) |

### 💃 Lady, Hunter & Tiger
| Move | Beats |
|------|-------|
| Lady | Hunter (charms) |
| Hunter | Tiger (shoots) |
| Tiger | Lady (devours) |

### 🐍 Snake, Water & Gun
| Move | Beats |
|------|-------|
| Snake | Water (drinks) |
| Water | Gun (rusts) |
| Gun | Snake (shoots) |

A one-line rules reminder is always shown under the tab bar for whichever mode is active, so you don't need to memorize this table.

---

## Project structure

```
rock-paper-scissors.html   # everything: markup, styles, and game logic
README.md                  # this file
```

It's intentionally a single file — easy to drop into any project, open directly from disk, or host anywhere that serves static files.

---

## Tech stack

- **HTML5** — structure and semantics
- **CSS3** — custom properties (CSS variables) drive all theming, so each mode's colors are swapped by changing a handful of variables rather than duplicating styles
- **Vanilla JavaScript (ES6+)** — no frameworks, no build tools, no npm packages
- **Google Fonts** — Space Grotesk (display) and Inter (body), loaded via CDN

---

## Customization

Because the game logic is data-driven, adding a fourth mode doesn't require touching the game engine at all. Open the `<script>` section and add a new entry to the `MODES` object:

```js
myMode: {
  label: 'Your Mode Name',
  words: ['moveA', 'moveB', 'moveC'],
  beats: { moveA: 'moveC', moveB: 'moveA', moveC: 'moveB' },
  verbs: { moveA: 'beats', moveB: 'beats', moveC: 'beats' },
  emoji: { moveA: '🔥', moveB: '💧', moveC: '🌪️' },
  chant: ['MoveA…', 'MoveB…', 'MoveC…', 'Go!'],
  tagline: 'Choose moveA, moveB, or moveC to start the round.'
}
```

Then:
1. Add a matching `<button class="mode-tab" data-mode="myMode">` to the tab bar in the HTML.
2. Add CSS variables `--moveA`, `--moveA-soft`, etc. (a main color and a soft background tint) for each new move, following the pattern already used for the existing moves.

The scoreboard, animations, confetti, and reset button all work automatically for any mode added this way.

---

## Browser support

Works in all modern evergreen browsers (Chrome, Firefox, Safari, Edge). No polyfills needed.

---

## License

Free to use, modify, and share.