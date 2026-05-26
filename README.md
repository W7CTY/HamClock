# HamClock Advanced

**A full-featured Amateur Radio Operations Center — browser app, native Fedora RPM, and Flatpak.**

Developed by **W7CTY** · [w7cty@outlook.com](mailto:w7cty@outlook.com)

---

## Packages

| File | Platform | Description |
|---|---|---|
| `hamclock-public.html` | Any browser | Self-contained HTML — no install needed |
| `hamclock-advanced-1.0.0-1.x86_64.rpm` | Fedora Linux | Native GTK4 app, install with `dnf` |
| `hamclock-advanced-flatpak-v1.0.0.tar.gz` | Fedora Linux | Flatpak build-from-source package |

---

## Browser Version — Quick Start

No installation or server required:

```bash
open hamclock-public.html       # macOS
xdg-open hamclock-public.html   # Linux
start hamclock-public.html      # Windows
```

Or just double-click the file. Enter your **callsign** and **grid square** in the banner — the map centres on your location automatically.

---

## Fedora RPM — Install

```bash
sudo dnf install hamclock-advanced-1.0.0-1.x86_64.rpm
```

`dnf` automatically installs all dependencies (`python3-gobject`, `gtk4`, `libadwaita`, `webkitgtk6.0`).

**Launch:**
```bash
hamclock-advanced
# or: Activities → HamClock Advanced
```

**Uninstall:**
```bash
sudo dnf remove hamclock-advanced

# To also remove all previous versions (including any HamClock Improved installs):
sudo bash /usr/share/hamclock-advanced/uninstall-hamclock.sh
```

---

## Fedora Flatpak — Install

> 📄 **Full illustrated install guide:** `INSTALL.pdf` (included in the Flatpak archive)

### Step 1 — Extract the archive

```bash
cd ~/Downloads
tar -xzf hamclock-advanced-flatpak-v1.0.0.tar.gz -C ~/Downloads
cd hamclock-flatpak-fixed
```

> **Note:** If the filename downloaded with an underscore (`hamclock-advanced-flatpak-v1.0.0_tar.gz`), use that exact name in the `tar` command.

### Step 2 — Run the installer

```bash
chmod +x install.sh
./install.sh
```

The script automatically:
- Installs `flatpak` and `flatpak-builder` (separate packages — both required)
- Adds the Flathub repository
- Installs **GNOME Platform 46** runtime
- Builds and installs HamClock Advanced

You will be prompted for your `sudo` password once.

### Step 3 — Launch

```bash
flatpak run org.w7cty.HamClockAdvanced
# or: Activities → HamClock Advanced
```

### Flatpak Uninstall

```bash
flatpak uninstall --user org.w7cty.HamClockAdvanced
```

### Flatpak Troubleshooting

| Error | Fix |
|---|---|
| `flatpak-builder: command not found` | `sudo dnf install -y flatpak-builder` then re-run `./install.sh` |
| `Cannot mkdir: Permission denied` | Make sure you `cd ~/Downloads` **before** running `tar` |
| `This version is already installed` | Run `flatpak uninstall --user org.w7cty.HamClockAdvanced` first |
| GNOME Platform 48 end-of-life warning | Use this package — it targets Platform 46 (supported) |
| Map tiles not loading | Internet connection required for NatGeo tiles |

---

## Features

### 📡 Station Identity
- Editable **Callsign** and **Grid Square** (Maidenhead 2–8 chars)
- GPS coordinates auto-calculated from grid square; map centres on your location
- Settings and theme preference saved across sessions

### ☀️ Solar & Space Weather
- Solar Flux Index (SFI), Sunspot Number (SSN)
- K-Index, A-Index, X-Ray flare class, Aurora activity
- Geomagnetic K-Index visual gauge (0–9)
- Space weather alert bar (Quiet / Unsettled / Storm)

### 📻 HF Band Conditions
- All bands 160m–6m with **day AND night** propagation quality — always visible side by side
- Active period highlighted with **NOW** badge and blue accent
- EXCELLENT / GOOD / FAIR / POOR / CLOSED pills with progress bars; MUF estimates

### 🗺️ Interactive Propagation Map
- **Esri National Geographic tile layer** — no API key needed
- Fully zoomable and pannable; auto-centres on your grid square
- **Gray-line terminator** updated every 60 seconds
- **Great-circle DX paths** to static beacon stations
- **Maidenhead grid square** bounding box overlay
- Floating toolbar (right side): Gray Line · DX Paths · Grid Sq · Recenter · **⤢ Expand**
- Map expandable to 620 px via toolbar button or ⚙ Settings

### 📊 Live DX Cluster Spots
- Up to **25 spots** displayed with auto-refresh every 4.5 seconds
- Band filter: ALL / 160M / 80M / 40M / 20M / 15M / 10M / 6M
- Mode filter: DX Spots / FT8+FT4 / CW
- DXCC entity count; new-spot flash animation

### 🕐 World Clocks
- **Slot 1: UTC** and **Slot 2: Local** (auto-derived from grid longitude) — locked
- Slots 3–8: **user-selectable** from 24 worldwide timezones
- Click **✎ EDIT** to add, remove, or change clocks (saved to browser storage)

### 🌅 Sunrise / Sunset
- Calculated from GPS coordinates derived from grid square
- Shows rise time, set time, and total day length in UTC

### 📝 Quick QSO Logger
- **Modes:** FT8, FT4, RTTY, PSK31, JS8, SSB, CW, AM, DMR, D-STAR, C4FM, FM
- **Operation Type:** N/A, POTA, SOTA, Field Day, Other (free-text)
- **LOG QSO (LOCAL)** — session counter, no network needed
- **LOG & UPLOAD TO QRZ** — posts ADIF record to QRZ Logbook API

### ⚙️ Settings — Gear Menu
- **Dark Mode** toggle (persisted between sessions)
- **Font Size:** 6 steps — 100% / 115% / 130% / 150% / 175% / **200%**
- **Expand Map** toggle
- **QRZ Login & API Key** — connect QRZ Logbook for QSO upload
- **My Station Settings** — re-open the callsign/grid wizard
- **Instructions** — full in-app help modal (6 sections)
- **Share This App** — shareable URL with callsign & grid embedded

### 📰 DX Wire Ticker
- Scrolling ticker bar always displayed in **bright gold** text on **black** background
- **Red border** (top and bottom) — consistent in both light and dark mode

### 📱 Responsive Layout
- Single-column at ≤ 900 px; extra-compact at ≤ 480 px
- Pinch-to-zoom on touch devices

---

## Keyboard Shortcuts (Fedora Native App)

| Key | Action |
|---|---|
| `F5` | Reload |
| `F11` | Toggle fullscreen |
| `Esc` | Exit fullscreen |
| `Ctrl +` | Zoom in |
| `Ctrl −` | Zoom out |
| `Ctrl 0` | Reset zoom |
| `Ctrl R` | Reload |
| `Ctrl Q` | Quit |

---

## Requirements

### Browser version
| Requirement | Details |
|---|---|
| Browser | Chrome 90+, Firefox 88+, Safari 14+, Edge 90+ |
| Internet | NatGeo map tiles and Google Fonts; core features work offline |
| Server | None |

### Fedora RPM / Flatpak
| Package | Version |
|---|---|
| `python3` | 3.8+ |
| `python3-gobject` | any |
| `gtk4` | any |
| `libadwaita` | any |
| `webkitgtk6.0` | Fedora 38–44 (2.40–2.52.x) |

---

## Technical Details

### Grid Square → GPS
Full Maidenhead system: 2-char (±100 km) → 4-char (±5 km) → 6-char (±500 m) → 8-char (±50 m). Local timezone auto-derived from grid longitude offset.

### QRZ Logbook API
Endpoint: `https://logbook.qrz.com/api` (POST, URL-encoded). API Access Key only — no username/password. Find your key at **QRZ Logbook → Settings → API Access Key**. CORS handled via direct call first, then three-proxy fallback chain (`allorigins.win` → `corsproxy.io` → `proxy.cors.sh`).

### Map
Tile provider: Esri National Geographic (`NatGeo_World_Map`). Library: Leaflet.js 1.9.4. Gray-line calculated from solar declination and current UTC. DX paths use 64-point geodesic interpolation.

### Flatpak Runtime
Uses GNOME Platform **46** (supported LTS). WebKit 6.0 primary, with WebKit 4.1 and 4.0 fallbacks for older Fedora versions.

---

## License

© 2026 W7CTY · All Rights Reserved

Personal and non-commercial use permitted. Please credit W7CTY if you share or adapt this work.

---

## Contact

**W7CTY** · [w7cty@outlook.com](mailto:w7cty@outlook.com)

*73 de W7CTY — Good DX!*
