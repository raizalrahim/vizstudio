# VIZSTUDIO — Music Visualizer

A browser-based, real-time music visualizer with modular frequency panels, stem support, live microphone input, background images, presentation mode, and full per-panel customization. No installation required. No data leaves your device. Deployable as a single HTML file.

🌐 **Live at [vizstudio.vercel.app](https://vizstudio.vercel.app)**

---

## Quick Start

1. Open the app in any modern browser
2. Drop a music file onto the upload zone or click to browse
3. Hit **▶** to play
4. Watch your panels react in real time
5. Optionally load individual stem files into panels for per-instrument visualization
6. Or use **🎤 USE MICROPHONE** from the ≡ menu for live mic input

**Supported audio formats:** MP3 · WAV · FLAC · OGG · M4A · AAC

---

## Header Controls

| Control | Description |
|---|---|
| **Mode Badge** | Current audio state — NO FILE / FULL MIX / MIX + N STEMS / N STEMS ONLY / MIC LIVE |
| **⛶ PRESENT** | Enter presentation mode |
| **≡ Menu** | All other controls |

**Inside the ≡ Menu:**

| Item | Description |
|---|---|
| ＋ ADD PANEL | Add a new frequency panel |
| HIDE / SHOW UPLOAD | Toggle the upload zone |
| 🎤 USE MICROPHONE | Switch to live mic input |
| 💾 SAVE LAYOUT | Export panel config as JSON |
| 📂 LOAD LAYOUT | Import a saved layout JSON |
| 📖 HOW TO USE | In-app help guide |
| ↺ RESET | Clear everything and start fresh |

---

## Frequency Panels

Each panel independently visualizes a specific frequency band.

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

| Type | Description |
|---|---|
| **Bars** | Frequency bar chart with gradient fill |
| **Wave** | Glowing time-domain waveform |
| **Circle** | Radial shape that pulses with energy |
| **Mirror Bars** | Bars mirrored above and below center |
| **Blob** | Organic morphing shape that breathes and pulses with audio energy |
| **Oscilloscope** | Raw audio signal trace |
| **Spectrum Fill** | Filled frequency area with gradient |
| **Radial Bars** | Bars radiating outward from center |

---

## Panel Controls

| Button | Action |
|---|---|
| ⠿ | Drag to reorder panels |
| ⧉ | Duplicate panel with all settings copied |
| 🔇 | Mute / unmute stem audio |
| ⚙ | Open / close settings drawer |
| ⛶ | Fullscreen for this panel only |
| ✕ | Remove panel and unload its stem |

---

## Per-Panel Settings

Open the ⚙ settings drawer on any panel:

- **Viz Type** — switch visualization style
- **Color 1 & Color 2** — gradient colors
- **Sensitivity** — reactivity (0.2–3.0)
- **Label** — rename the panel
- **BG Image** — static background image behind the visualization

**Background Image options:**
- Formats: JPG, PNG, WebP
- **BG Opacity** — 5% to 90% (default 35%)
- **BG Fit** — Cover, Contain, or Fill
- Best with dark or textured images

> Background images are not saved in layout JSON exports and must be reloaded manually.

---

## Stem Support

Each panel can have its own stem file for accurate per-instrument visualization.

**Audio routing:**

| Scenario | What you hear |
|---|---|
| Full mix only | Main track through speakers |
| Full mix + stems | Main track audible · stems silent |
| Stems only | All stems audible, reconstructing the song |
| Mic active | Mic input only · stems bypassed |

**Stem slot controls:**
- **+ LOAD STEM** — assign a stem file
- **↺ CHANGE** — swap stem without losing settings
- **✕** — remove stem, panel reverts to full mix
- **🔇** — mute / unmute this stem independently

**Stem sync indicator:**
- 🟢 Pulsing green — playing
- 🟠 Orange — paused
- ⚫ Dark — no stem loaded

> **Tip:** Use LALAL.AI, Moises.app, or Audiostrip to split your song into stems before loading them here.

---

## Microphone Input

Switch all panels to live microphone visualization without uploading any files.

**How to use:**
1. Open ≡ menu → **🎤 USE MICROPHONE**
2. Browser prompts for mic permission — allow it
3. Any playing audio stops
4. Red **🎤 MICROPHONE LIVE** bar appears with pulsing dot
5. All panels instantly visualize live mic input

**To stop mic:**
- Click **⏹ STOP MIC** in the mic bar
- Or open ≡ menu → **🎤 USE MICROPHONE** again
- Or click **↺ RESET**

**Important notes:**
- Mic audio is never routed to speakers — no feedback loop
- Stems are bypassed while mic is active
- All panel settings, viz types, and colors stay intact
- Returning to file mode restores everything exactly as it was
- Works best with headphones or in a quiet environment

**Browser mic permission:**
- Requires HTTPS — works automatically on `vizstudio.vercel.app`
- Safari on iOS/iPadOS supports `getUserMedia` — permission prompt may look different
- If permission is denied, a toast notification will appear

---

## Player Controls

- **▶ / ⏸** — Play and pause all audio simultaneously
- **Progress bar** — Click to seek · all stems seek together
- **Volume** — Controls overall output level
- **⏏ CHANGE TRACK** — Swap main track without resetting panels
- **✕ CLEAR TRACK** — Remove main track only · panels and stems stay intact

---

## Save & Load Layout

**💾 SAVE LAYOUT** — exports `vizstudio-layout.json`

**📂 LOAD LAYOUT** — rebuilds panels from a saved file

| Saved ✅ | Not saved ❌ |
|---|---|
| Panel order | Main track audio |
| Band selection | Stem audio files |
| Viz type | Background images |
| Colors (1 & 2) | Playback position |
| Sensitivity | |
| Custom labels | |
| Stem filenames (as hints) | |

> Audio files and images can't be saved — browsers block local file access between sessions for security reasons. Stem filename hints appear in each panel after loading so you know which files to reload.

---

## Presentation Mode

Click **⛶ PRESENT** to enter full-screen visualization mode.

**What is hidden:** header, player bar, upload zone, panel headers, stem slots, settings drawers, borders

**What stays:** pure canvas visualizations filling the entire screen

**Panel grid in presentation mode:**

| Panels | Layout |
|---|---|
| 1 | Full screen |
| 2 | 2 equal columns |
| 3 | 2 top + 1 full width below |
| 4 | 2×2 perfect grid |
| 5 | 3 top + 2 equal below |
| 6 | 3×2 perfect grid |
| 9 | 3×3 perfect grid |

Panels use LCM-based column spanning so every row fills the screen uniformly — no gaps, no uneven sizing.

Screen width column caps: ≤900px = 2 cols · ≤1200px = 3 cols · >1200px = 4 cols

**To exit:** press **Escape** or click **✕ EXIT PRESENTATION** (bottom-right, hover to reveal)

> Play your music before entering presentation mode — controls are hidden inside it.

---

## Performance Guide

| Device | Comfortable Panels | Notes |
|---|---|---|
| Desktop — dedicated GPU | 10–20 | Browser is the ceiling |
| Mid-range laptop | 6–10 | Avoid all-particle layouts |
| iPad Pro M4 | 8–10 | Safari engine is the constraint |
| iPad Air M3 / 11" | 4–6 | Max 3 cols in landscape |
| Android tablet | 6–10 | Chrome handles it well |
| Phone | Not recommended | Best on tablet or desktop |

**Viz types by GPU weight (lightest → heaviest):**
Oscilloscope → Bars → Wave → Mirror Bars → Blob → Spectrum Fill → Radial Bars → Circle

> Background images add slight per-panel rendering overhead. Use sparingly on lower-end devices.

---

## Privacy

All audio, image, and microphone processing runs entirely in your browser. Nothing is uploaded to any server. No data is collected or transmitted. Your music, images, and mic audio never leave your device.

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
| Android Chrome | ✅ Full support |

> On iPad, use files stored in the **Files app** or **iCloud Drive**. Apple Music library files are not accessible from the browser. Microphone requires HTTPS — provided automatically by Vercel.

---

## Deployment

Single HTML file — no build step, no dependencies, no framework.

### Vercel

**Option 1 — Drag & Drop**
1. Sign in to [vercel.com](https://vercel.com)
2. Click **Add New → Project**
3. Drag `index.html` onto the page

**Option 2 — GitHub (recommended)**
1. Repo with `index.html` at root → connect to Vercel
2. Every push auto-redeploys

**Option 3 — CLI**
```bash
npm i -g vercel
cd your-folder
vercel
```

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
