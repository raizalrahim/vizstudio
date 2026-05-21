# VIZSTUDIO — Music Visualizer

A browser-based, real-time music visualizer with modular frequency panels, stem support, background images, presentation mode, and full per-panel customization. No installation required. No data leaves your device. Deployable as a single HTML file.

---

## Quick Start

1. Open the app in any modern browser
2. Drop a music file onto the upload zone or click to browse
3. Hit **▶** to play
4. Watch your panels react in real time
5. Optionally load individual stem files into each panel for per-instrument visualization

**Supported audio formats:** MP3 · WAV · FLAC · OGG · M4A · AAC

---

## Header Controls

The header stays minimal with two always-visible controls:

| Control | Description |
|---|---|
| **Mode Badge** | Shows current audio state (NO FILE / FULL MIX / MIX + N STEMS / N STEMS ONLY) |
| **⛶ PRESENT** | Enter presentation mode — hides all UI, shows only visualizations |
| **≡ Menu** | Opens the hamburger dropdown with all other controls |

**Inside the ≡ Menu:**

| Item | Description |
|---|---|
| ＋ ADD PANEL | Add a new frequency panel |
| HIDE / SHOW UPLOAD | Toggle the upload zone visibility |
| 💾 SAVE LAYOUT | Export panel configuration as a JSON file |
| 📂 LOAD LAYOUT | Import a previously saved layout JSON file |
| ↺ RESET | Clear everything and start fresh |

---

## Frequency Panels

Each panel independently visualizes a specific frequency band. Add as many as your device can handle comfortably.

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

## Visualization Types

Each panel supports 8 visualization styles:

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

## Panel Controls

| Button | Action |
|---|---|
| ⠿ | Drag handle — drag to reorder panels |
| ⧉ | Duplicate panel with all settings copied |
| 🔇 | Mute / unmute stem audio (visible when stem is loaded) |
| ⚙ | Open / close settings drawer |
| ⛶ | Toggle fullscreen for this panel only |
| ✕ | Remove panel |

---

## Per-Panel Settings

Open the ⚙ settings drawer on any panel to customize:

- **Viz Type** — switch visualization style at any time
- **Color 1 & Color 2** — gradient color control
- **Sensitivity** — how aggressively the panel reacts to audio (0.2–3.0)
- **Label** — rename the panel to anything
- **BG Image** — load a static background image behind the visualization

**Background Image settings:**
- Accepted formats: JPG, PNG, WebP
- **BG Opacity** — 5% to 90% (default 35%)
- **BG Fit** — Cover, Contain, or Fill
- Best with dark, moody, or textured images

> Background images are not saved in layout JSON exports and must be reloaded manually after loading a saved layout.

---

## Stem Support

Each panel can have its own stem file for accurate per-instrument visualization.

**How stems work:**

Click **+ LOAD STEM** in any panel's stem slot to assign a stem audio file to that panel. The panel then visualizes only that stem's frequencies instead of the full mix.

**Audio routing by scenario:**

| Scenario | What you hear |
|---|---|
| Full mix only | Main track through speakers |
| Full mix + stems | Main track audible · stems silent (analysis only) |
| Stems only | All stems play audibly, reconstructing the song |

**Stem slot controls:**
- **+ LOAD STEM** — assign a stem file to this panel
- **↺ CHANGE** — swap stem without losing panel settings
- **✕** — remove stem, panel reverts to full mix analysis
- **🔇** — mute / unmute this stem's audio independently

**Stem sync indicator:**
- 🟢 Pulsing green — stem is live and playing
- 🟠 Orange — stem loaded but paused
- ⚫ Dark — no stem loaded

**Frequency bands and stems:**
The band setting acts as a filter on top of the stem. A drums stem on a HIGHS panel shows only the cymbal and hi-hat content of that stem. A vocals stem on a BASS panel will show almost nothing — vocals don't live there. Use band settings creatively to isolate exactly the part of each instrument you want to visualize.

> **Tip:** Use LALAL.AI, Moises.app, or Audiostrip to split your songs into stems before loading them here.

---

## Player Controls

- **▶ / ⏸** — Play and pause all audio simultaneously
- **Progress bar** — Click to seek · all audio including stems seeks together
- **Volume** — Controls overall output level
- **⏏ CHANGE TRACK** — Swap the main track without resetting panels
- **HIDE / SHOW UPLOAD** — Toggle upload zone (in ≡ menu)

---

## Save & Load Layout

**💾 SAVE LAYOUT** exports a `vizstudio-layout.json` file containing your full panel configuration.

**📂 LOAD LAYOUT** rebuilds your panels instantly from a saved file.

**What is saved:**

| Saved ✅ | Not saved ❌ |
|---|---|
| Panel order | Main track audio |
| Band selection | Stem audio files |
| Viz type | Background images |
| Colors (1 & 2) | Playback position |
| Sensitivity | |
| Custom labels | |
| Stem filenames (as reload hints) | |

After loading a layout, panels with previously assigned stems show **⚠ RELOAD: filename** in the stem slot as a reminder of which file to re-assign.

> Audio files and images can't be saved to JSON — browsers block JavaScript from storing local file references between sessions for security reasons.

---

## Presentation Mode

Click **⛶ PRESENT** to enter a clean full-screen visualization view.

**What is hidden:**
- Header, player bar, upload zone
- Panel headers, stem slots, settings drawers
- Add panel card, section labels, panel borders

**What stays:**
- Pure canvas visualizations filling the entire screen
- Panels automatically arrange into the most balanced grid layout for the number of panels open
- A faint **✕ EXIT PRESENTATION** button in the bottom-right corner (becomes visible on hover)

**Panel layout in presentation mode:**

| Panels | Grid |
|---|---|
| 1 | Full screen |
| 2 | 2 columns |
| 4 | 2×2 |
| 6 | 3×2 |
| 9 | 3×3 |

**To exit presentation mode:**
- Press **Escape**
- Click **✕ EXIT PRESENTATION** (bottom-right)

> Play your music before entering presentation mode — controls are hidden inside it.

---

## Performance Guide

| Device | Comfortable Panels | Notes |
|---|---|---|
| Desktop — dedicated GPU | 10–20 | Browser is the ceiling, not hardware |
| Mid-range laptop | 6–10 | Avoid all-particle layouts |
| iPad Pro M4 | 8–10 | Safari engine is the main constraint |
| iPad Air M3 | 4–6 | Stick to Bars, Wave, Oscilloscope |

**Viz types by GPU weight (lightest → heaviest):**
Oscilloscope → Bars → Wave → Mirror Bars → Spectrum Fill → Radial Bars → Circle → Particles

> Background images add a small per-panel overhead. Use sparingly on lower-end devices.

---

## Privacy

All audio and image processing runs entirely in your browser. Nothing is uploaded to any server. No data is collected or transmitted. Your music and images never leave your device.

---

## Browser Compatibility

| Browser | Support |
|---|---|
| Chrome (desktop) | ✅ Full |
| Firefox (desktop) | ✅ Full |
| Edge (desktop) | ✅ Full |
| Safari (desktop) | ✅ Full |
| Chrome / Firefox (iOS & iPadOS) | ⚠️ Runs on Safari engine |
| Safari (iOS & iPadOS) | ⚠️ Works with some audio limitations |

> On iPad, use files stored in the **Files app** or **iCloud Drive**. Apple Music library files are not accessible from the browser due to iOS restrictions.

---

## Deployment

VIZSTUDIO is a single HTML file — no build step, no dependencies, no framework.

### Vercel

**Option 1 — Drag & Drop**
1. Sign in to [vercel.com](https://vercel.com)
2. Click **Add New → Project**
3. Drag `index.html` onto the page
4. Done — live URL provided instantly

**Option 2 — GitHub (recommended for updates)**
1. Create a repo with `index.html` at the root
2. Connect the repo to Vercel
3. Every push auto-redeploys

**Option 3 — CLI**
```bash
npm i -g vercel
cd your-folder
vercel
```

**Folder structure:**
```
your-project/
├── index.html
└── README.md
```

---

## Recommended Stem Tools

| Tool | Notes |
|---|---|
| [LALAL.AI](https://lalal.ai) | High quality · free tier |
| [Moises.app](https://moises.app) | Popular with producers · free tier |
| [Audiostrip](https://audiostrip.co.uk) | Simple · free |
| [Demucs by Meta](https://github.com/facebookresearch/demucs) | Open source · runs locally in Python |
