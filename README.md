# Night Shift

A browser-based first-person horror game built as an AP CSA final project. The
player works the late shift at an abandoned grocery store, must find items to
unlock the exit door, and survive mannequins that only move when you aren't
looking at them.

The game runs as a **single HTML file**. No build system, no package manager,
no install — just open `practice.html` in a modern browser.

## Running

Two options:

1. **Double-click `practice.html`** in Finder. It will open in your default
   browser via `file://`.
2. Or serve the folder locally if you prefer:
   ```bash
   python3 -m http.server 8000
   ```
   then visit `http://localhost:8000/practice.html`.

Three.js is loaded from `unpkg.com` via an `importmap`, so the page needs
internet access on first load.

## Controls

| Key / Mouse | Action |
| --- | --- |
| `W` `A` `S` `D` | Move |
| Mouse | Look |
| `Shift` (hold) | Sprint (5 s stamina, regenerates while walking) |
| `1`–`8` | Switch inventory slot |
| Left click | Use / pick up whatever the crosshair is on |
| `Esc` | Release the mouse |

## How to play

- The exit door behind the player spawn has three blockages: **wooden
  boards**, a **padlock**, and a **fingerprint keypad**.
- Find a **crowbar** to rip the boards off, a **key** to break the padlock,
  and a severed **arm** to fool the keypad.
- The arm drops from the red mannequin once it's been shot — the gun isn't
  implemented yet.
- Mannequins are quantum-locked: they freeze while you look at them and
  advance when you look away. They're faster than you walk but slower than you
  sprint, so sprinting buys an escape.

## Code layout

- `practice.html` — the entire game. All HTML/CSS/JavaScript lives in one
  file by design (single-file for easy hosting / sharing).
- `FinalPrompt.md` — running log of the prompts that shaped each iteration of
  the game. Treat as a deliverable, not just notes.

Inside `practice.html`, search for these region banners to find each subsystem:

- `CONFIG` — top-of-script constants (store dimensions, lighting, speeds, …).
- `SCENE / CAMERA / RENDERER`
- `LIGHTING` and the `Flashlight` block
- `FLOOR + CEILING`, `NIGHT SKY texture`, `CONCRETE WALL TEXTURE`
- `WALLS`, `EXIT DOOR`, `SHELVES`, `WALL-MOUNTED SHELVES`, `CHECKOUT AREA`,
  `TABLES`
- `MANNEQUINS` (sprite + AI)
- `PICKUPS` (items + spawn surfaces)
- `CONTROLS` and the inventory / hotbar
- `MOVEMENT + COLLISION`
- `MAIN LOOP`

Most gameplay tweaks live in the `CONFIG` block at the top.

## Author

Sohan Nellaturu — AP Computer Science A.
