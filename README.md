# Schrödinger's Cat — A Quantum Superposition Game

**Play it:** https://jocular-lamington-829acc.netlify.app/

A retro-arcade browser game that teaches quantum superposition, measurement, and
entanglement to people with no physics background. A cat is sealed in a box with a quantum
trigger. Until you look, it is alive *and* dead. Your job is to guess the outcome before
the box opens, and to get better than chance by learning to read the physics.

Built by **Ryan Agnew, Salar Kafaei, and Xiao Zhou** for the **UBC Quantum Game Jam**
(June 2026). Placed **second of ~30 teams** and was selected for the UBC showcase.

The whole game is one self-contained `index.html`: no build step, no dependencies, no
network requests apart from one Google Font. Double-click it or host it anywhere static.

---

## How to play

| Action | Key |
| --- | --- |
| Guess ALIVE / DEAD / ASLEEP | **A** / **D** / **S** (or click) |
| Set stake 1× / 2× / 3× | **1** / **2** / **3** |
| Hadamard / Pauli-X / Probe / CNOT | **H** / **X** / **P** / **C** |
| Flip result (after observing, X armed) | **X** |
| Mute | **M** |

Level 1 is a pure 50/50 tutorial. Score 500 points and the box starts leaking information.

## Where the physics is

The cat's state is not decided when the round starts. It is decided at the moment you
observe, by drawing against the amplitude of the alive component: `rng() < |α|²`. That is
Born's rule, and it is the only line in the game that "collapses" anything.

- **Cues (Level 2+).** The atom spins faster and the Geiger counter ticks faster as decay
  probability rises; the box glows green when ALIVE is likely and magenta when DEAD is
  likely. A good player stops guessing and starts reading the amplitude.
- **Gates as power-ups**, unlocked by streaks:
  - **Hadamard** resets the state to an exact 50/50 superposition.
  - **Pauli-X** arms a bit-flip you can apply once after observing.
  - **Measurement probe** reveals |α|² as a percentage but forfeits the streak bonus
    (information at the cost of disturbing the game state).
  - **CNOT** switches the entanglement type in two-cat rounds.
- **Decoherence timer (Level 3+).** Wait too long and the wave function collapses on its own.
- **Entangled rounds (Level 4+).** Two cats share a Bell state. |Φ+⟩ means both end up the
  same; |Ψ+⟩ means opposite. The second cat is forced by the first.
- **Qutrits (Level 5+).** Some cats can also be ASLEEP: three outcomes, three amplitudes.
- **Boss rounds.** Many-Worlds (guess how many of five cats survive), Quantum Zeno (rapid
  repeated observations pull the state toward what you keep seeing), and a hard decoherence
  timer.

## Other features

- Six levels with a progress bar, stakes, combos, and a streak flame
- **Daily Challenge**: 20 rounds on a date-seeded RNG so everyone plays the same
  sequence, with a shareable result line
- Achievements, lifetime stats, and unlockable cat skins, all saved in `localStorage`
- Chiptune soundtrack and sound effects synthesized live with the Web Audio API (no audio
  files)
- CRT scanlines, screen shake, particle bursts, and a cat that gets dropped into the box
  by a tractor beam

## Stack

Vanilla JavaScript, HTML, CSS, SVG sprites, Web Audio API. Built with Claude Code as a
pair-programmer.

## Credits

Ryan Agnew · Salar Kafaei · Xiao Zhou
Inspired by Erwin Schrödinger's 1935 thought experiment.
