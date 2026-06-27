# Table Goes to Hollywood

A pixel-art browser game where you play a **sentient wooden table** galloping across a
GTA‑style Los Angeles to plant yourself on the **HOLLYWOOD** sign — flipping SUVs,
bowling over interns, and outrunning a parody AAA publisher's Legal Defense Units.

**▶ Play it: https://zacharybird.com/table-goes-to-hollywood.html**

The whole game is **one self-contained HTML file** — no build step, no bundler, no
backend. Open it in any modern browser and it runs.

---

## How to play

Reach the HOLLYWOOD sign before the publisher's lawyers corner you. Smash props for
cash and combos; the more chaos, the higher your WANTED level — and the harder the
Legal Defense Units chase. Get cornered and you're either **WASTED** (you wipe out) or
**BUSTED** (hauled off and shaken down for your cash).

### Controls

| | Desktop | Mobile |
|---|---|---|
| Move | `WASD` / arrow keys | left virtual stick |
| Look | mouse | drag the screen |
| Gallop (sprint) | `Shift` | sprint button |
| Hijack a nearby car | `E` | hijack button |
| First / third person | `C` | camera button |
| Pause | `Esc` | pause button |
| Mute | `M` | mute button |

---

## Tech

- **[Three.js](https://threejs.org/) (r128)** — WebGL rendering, loaded from CDN with a
  pinned fallback.
- **Procedural everything** — the city grid, buildings, vehicles, pedestrians, audio,
  and the table itself are generated in code; there are no external art or sound assets.
- **Pixel-art pipeline** — the scene renders to a low-resolution buffer and is
  upscaled nearest-neighbour for a crunchy retro look.
- **One file, zero build** — all HTML, CSS, and JS live in
  `table-goes-to-hollywood.html`. Desktop and mobile (touch) are both supported.

### Hardening (because it's public-facing)

- **Content-Security-Policy** locking scripts/styles/fonts/images/connections to
  `self` plus the Three.js CDNs, Google Fonts, and analytics only.
- **Subresource Integrity** (SHA‑384) on the CDN script and its fallback.
- **Graceful failure** — a friendly overlay if WebGL is unavailable or the 3D engine
  fails to load, instead of a blank screen.

---

## Run it locally

No tooling required — just serve the folder (browsers block some features on
`file://`):

```sh
python3 -m http.server 8000
# then open http://localhost:8000/table-goes-to-hollywood.html
```

---

## About / legal

This is an **original parody**, built for fun and as a hands-on experiment in shipping
a complete game with AI-assisted development. It is **not affiliated with, endorsed by,
or associated with** any game publisher, studio, or franchise. It contains no
copyrighted or trademarked assets — all art, audio, fonts, names, and code are original
or openly licensed. The "AAA publisher" and its lawyers are fictional send-ups; any
resemblance to a real franchise is the joke.

## License

Licensed under [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](LICENSE).
You're free to play, share, and remix it with attribution — just not for commercial use.
