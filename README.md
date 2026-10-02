# Terminal-Planet-Collision-Sim

A real-time 3D physics simulation rendered entirely in the terminal using ASCII art. Planets, moons, and irregular bodies orbit, collide, merge, and fragment — all in your shell.

---

## What it does

- Simulates gravitational attraction between multiple bodies with configurable mass, radius, and shape
- Detects and resolves collisions: bodies can merge, bounce, or shatter depending on parameters
- Projects 3D positions onto a 2D ASCII canvas in real time
- Supports multiple body shapes: spheres, ellipsoids, rough/cratered surfaces
- Runs entirely in the terminal, no GUI required

---

## Core components

**Physics engine** — gravitational force calculation (n-body), collision detection, response (merge vs elastic vs fragmentation), and a fixed timestep integration loop (Verlet or RK4)

**3D to ASCII renderer** — project 3D coordinates to 2D terminal space, shade surfaces using ASCII density gradients (` . : ; + * # @`), handle depth sorting so nearer bodies occlude farther ones

**Body system** — each body has mass, position, velocity, shape, and a surface shader; shape affects collision geometry and how it renders

**Camera** — rotatable viewpoint, zoom, and tracking mode to follow a body

---

## Possible languages and stacks

| Language | Why it fits | Notes |
|---|---|---|
| **C** | Raw speed, direct terminal control, classic systems choice | ncurses for terminal handling; good if the team wants low-level |
| **C++** | Speed + OOP for body/scene abstractions | Easier to structure than C, still fast enough for real-time |
| **Rust** | Memory safe, fast, good ecosystem | `crossterm` or `ratatui` for terminal; fits the Zed crowd |
| **Python** | Fastest to prototype | `curses` stdlib; numpy for physics vectors; slower but fine for small n |
| **Go** | Easy concurrency for render loop vs physics loop | `tcell` for terminal; clean for a first systems project |

**Recommended starting point:** Python to prove the physics and renderer work, then port the hot path to Rust or C++ if performance needs it.

---

## v1 scope

Two bodies only. Pick two presets, watch them interact.

**Presets**
- Earth + Mars
- Sun + Jupiter
- Rogue asteroid + Earth
- Neutron star + gas giant
- Binary star system

Each preset defines mass, radius, initial velocity, and surface texture. Collision outcome (merge, bounce, or shatter) is determined by relative mass and impact speed.

Fixed camera, real-time ASCII render at stable framerate, configurable via CLI flags.

**Extension path**
- v2: third body, n-body gravity
- v3: custom body creator (set your own mass, radius, name)
- v4: fragmentation and debris fields

---

## Why it is novel

No well-maintained open source ASCII 3D physics sim exists. There are toy scripts and one-off gists but nothing structured, extensible, or collaborative. This is a project you can actually demo to your friends.

---

## Open questions for the first meeting

- True 3D projection or layered 2D illusion?
- Roll our own physics or wrap an existing engine?
- Which language does the team actually want to write?
- What does fragmentation look like in ASCII?
