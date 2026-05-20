# VIZSTUDIO — Music Visualizer

A browser-based, real-time music visualizer with modular frequency panels, stem support, and full customization. No installation required. No data leaves your device.

---

## Getting Started

1. Open the app in any modern browser
2. Drop a music file onto the upload zone or click to browse
3. Hit play and watch your panels react in real time
4. Optionally load individual stem files into each panel for per-instrument visualization

Supported formats: **MP3 · WAV · FLAC · OGG · M4A**

---

## Features

### Modular Frequency Panels
Each panel independently visualizes a specific frequency band of your audio. Add as many panels as you want using the **+ ADD PANEL** button. Panels can be freely arranged, customized, duplicated, or removed.

**Available frequency bands:**

| Band | Frequency Range | Best For |
|---|---|---|
| Sub Bass | 20–60 Hz | Kick drum low-end, deep rumble |
| Bass | 60–250 Hz | Bass guitar, kick body |
| Low Mids | 250–500 Hz | Warmth, rhythm guitars |
| Mids | 500Hz–2k Hz | Vocals, snare, melodic elements |
| High Mids | 2k–4k Hz | Presence, attack, snare crack |
| Highs | 4k–20k Hz | Cymbals, hi-hats, air |
| Full Range | 20–20k Hz | Entire frequency spectrum |

---

### Visualization Types
Each panel supports 8 visualization styles, selectable per panel:

| Type | Description |
|---|---|
| **Bars** | Classic frequency bar chart with gradient fill |
| **Wave** | Glowing time-domain waveform |
| **Circle** | Radial frequency shape that pulses with energy |
| **Mirror Bars** | Bars mirrored above and below center |
| **Particles** | Energy-reactive particles that burst upward |
| **Oscilloscope** | Raw audio signal trace |
| **Spectrum Fill** | Filled frequency area with gradient |
| **Radial Bars** | Bars radiating outward from a center point |

---

### Per-Panel Customization
Every panel has its own settings drawer (⚙ button):

- **Viz Type** — switch visualization style at any time
- **Color 1 & Color 2** — control gradient colors
- **Sensitivity** — how aggressively the panel reacts to audio (0.2 to 3.0)
- **Label** — rename the panel to anything you want
- **BG Image** — load a static background image behind the visualization

**Background Image options:**
- Accepted formats: JPG, PNG, WebP
- **BG Opacity** slider — 5% to 90% (default 35% keeps the visualization readable)
- **BG Fit** — Cover (fills panel), Contain (fits inside), Fill (stretches)
- **✕** — removes the background image
- Best results with dark, moody, or textured images — busy or bright images can clash with the visualization

> **Note:** Background images are not saved in layout JSON exports due to file size constraints. They will need to be reloaded manually after loading a saved layout.

---

### Stem Support
Each panel can have its own stem file loaded independently of the main track.

**How it works:**

- Click **+ LOAD STEM** in any panel's stem slot to assign a stem file
- The panel will then visualize only that stem's audio instead of the full mix
- Stems without a main track play audibly and reconstruct the song
- Stems with a main track run silently — the main track plays through the speakers

**Audio routing:**

| Scenario | What you hear |
|---|---|
| Full mix only | Main track through speakers |
| Full mix + stems | Main track only; stems run silently for visuals |
| Stems only, no main track | All stems play audibly, reconstructing the song |

**Per-stem controls:**
- **🔇 Mute button** — silence individual stems without removing them
- **↺ CHANGE** — swap the stem file without losing panel settings
- **✕** — remove the stem, reverting the panel to visualizing the full mix

**Stem sync indicator (dot in stem slot):**
- 🟢 Green pulsing — stem is live and playing
- 🟠 Orange — stem loaded but paused
- ⚫ Dark — no stem loaded on this panel

> **Tip:** Use a free stem separation tool like LALAL.AI, Moises.app, or Audiostrip to split your song into drums, vocals, bass, and other stems before loading them here.

---

### Panel Actions

| Button | Action |
|---|---|
| ⠿ (drag handle) | Drag to reorder panels in the grid |
| ⧉ | Duplicate panel with all settings copied |
| ⚙ | Open / close settings drawer |
| ⛶ | Toggle fullscreen mode for that panel |
| ✕ | Remove the panel |

---

### Player Controls

- **▶ / ⏸** — Play and pause all audio (main track + all stems) simultaneously
- **Progress bar** — Click anywhere to seek; all audio seeks together
- **Volume slider** — Controls overall output volume
- **⏏ CHANGE TRACK** — Swap the main track without resetting your panel layout
- **HIDE UPLOAD / SHOW UPLOAD** — Toggle the upload zone visibility (useful when working stems-only)

---

### Save & Load Layout

Your panel configuration can be saved as a `.json` file and reloaded in any future session.

**💾 SAVE LAYOUT**
- Downloads a `vizstudio-layout.json` file to your device
- Saves every panel's band, viz type, colors, sensitivity, label, and order
- Also records stem filenames as reload reminders

**📂 LOAD LAYOUT**
- Opens a file picker for `.json` layout files
- Rebuilds all panels instantly with all settings restored
- If panels had stems assigned, each stem slot shows **⚠ RELOAD: filename** as a reminder of which file to re-assign
- Toast notification confirms how many stems need reloading

**What gets saved and restored:**

| Saved ✅ | Not saved ❌ |
|---|---|
| Panel order | Main track audio file |
| Band selection | Stem audio files |
| Viz type | Background images |
| Colors (1 & 2) | Playback position |
| Sensitivity | |
| Custom labels | |
| Stem filenames (as hints) | |

> **Why audio and images aren't saved:** Browsers deliberately block JavaScript from storing or re-accessing local files between sessions for security reasons. After loading a layout, simply re-upload your audio files and background images manually — the panel setup is already done for you.

**Typical workflow after loading a layout:**
1. Click **📂 LOAD LAYOUT** and select your `.json` file
2. Panels rebuild instantly
3. Drop your main track into the upload zone
4. Reload stems into their panels using the filename hints shown
5. Reload any background images into their panels

---

### Mode Badge
The header displays your current audio mode at a glance:

| Badge | Meaning |
|---|---|
| `NO FILE` | Nothing loaded yet |
| `FULL MIX` | Main track loaded, no stems |
| `MIX + N STEMS` | Main track plus stem files loaded |
| `N STEMS ONLY` | Stems only, no main track |

---

### Idle State
Panels show an animated placeholder with "WAITING FOR AUDIO" when no audio is loaded. This disappears automatically once any audio source is active.

---

### Reset
The **RESET** button clears everything — main track, all stems, all panels — and returns the app to its initial state. Saved layout files are not affected.

---

## Performance Guide

Performance depends on your device and browser. General recommendations:

| Device | Comfortable Panel Range | Notes |
|---|---|---|
| Desktop with dedicated GPU | 10–20 panels | Very capable, browser is the ceiling |
| Mid-range laptop | 6–10 panels | Avoid heavy particle effects across all panels |
| iPad Pro (M4) | 8–10 panels | Safari engine is the main constraint |
| iPad Air (M3) | 4–6 panels | Stick to bar and wave viz types |

**Viz types by GPU cost (lightest to heaviest):**
Oscilloscope → Bars → Wave → Mirror Bars → Spectrum Fill → Radial Bars → Circle → Particles

> **Tip:** Background images add a small rendering overhead per panel. On lower-end devices, use them sparingly.

---

## Privacy

All audio and image processing happens entirely in your browser. No files are uploaded to any server. No data is collected or transmitted. Your music and images never leave your device.

---

## Deployment

VIZSTUDIO is a single HTML file with no dependencies or build step.

### Vercel (Recommended)

**Option 1 — Drag & Drop**
1. Go to [vercel.com](https://vercel.com) and sign in
2. Click **Add New → Project**
3. Drag and drop `index.html` onto the page
4. Done — Vercel provides a live public URL instantly

**Option 2 — Via GitHub**
1. Create a GitHub repo with `index.html` at the root
2. Connect the repo to Vercel
3. Every push to GitHub auto-redeploys the app

**Option 3 — Vercel CLI**
```bash
npm i -g vercel
cd your-folder
vercel
```

### Folder Structure
```
your-project/
└── index.html
└── README.md
```
No `package.json`, no framework, no config needed.

---

## Browser Compatibility

| Browser | Support |
|---|---|
| Chrome (desktop) | ✅ Full support |
| Firefox (desktop) | ✅ Full support |
| Edge (desktop) | ✅ Full support |
| Safari (desktop) | ✅ Full support |
| Chrome / Firefox (iOS & iPadOS) | ⚠️ Uses Safari engine under the hood |
| Safari (iOS & iPadOS) | ⚠️ Works with some audio element limitations |

---

## Recommended Stem Separation Tools

| Tool | Notes |
|---|---|
| [LALAL.AI](https://lalal.ai) | High quality, free tier available |
| [Moises.app](https://moises.app) | Popular with musicians, free tier available |
| [Audiostrip](https://audiostrip.co.uk) | Simple, free vocal/instrumental separation |
| [Demucs by Meta](https://github.com/facebookresearch/demucs) | Open source, runs locally in Python |
