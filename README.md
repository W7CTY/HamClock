# HamClock Improved

**A modern, full-featured Amateur Radio Operations Center — runs entirely in your browser, no installation required.**

Developed by **W7CTY** · Contact: [w7cty@outlook.com](mailto:w7cty@outlook.com)

---

## Overview

HamClock Improved is a single-file HTML5 web application built for amateur radio operators. It provides real-time HF propagation conditions, solar indices, a live DX cluster spot feed, an interactive National Geographic world map with gray-line overlay, world clocks, and a quick QSO logger — all in one page.

Two themes are included:

| File | Theme |
|---|---|
| `hamclock-white.html` | Light theme — white background, gold banner |
| `hamclock-dark.html` | Dark theme — dark background, all-gold text |

---

## Features

### 📡 Station Identity
- **Callsign** — editable text field, updates map label in real time
- **Grid Square** — Maidenhead locator input (2–8 characters); automatically computes GPS coordinates and centers the map
- **GPS Coordinates** — latitude and longitude displayed in the banner, derived from the grid square

### ☀️ Solar & Space Weather
- Solar Flux Index (SFI)
- Sunspot Number (SSN)
- K-Index and A-Index
- X-Ray flare class
- Aurora activity level
- Color-coded alerts (Quiet / Unsettled / Storm)
- Geomagnetic K-Index gauge (0–9)

### 📻 HF Band Conditions
- All HF bands: 160m through 6m
- Day and night propagation quality bars (Excellent / Good / Fair / Poor / Closed)
- Maximum Usable Frequency (MUF) estimates
- Conditions automatically adjust based on solar data

### 🗺️ Interactive World Map
- **National Geographic tile layer** (Esri NatGeo World Map) — no API key required
- **Fully zoomable and pannable** — scroll wheel, pinch-to-zoom, or +/− controls
- **Auto-centers on operator's grid square** when grid is updated
- **Gray-line terminator** — animated day/night boundary updated every 60 seconds, with sun position marker
- **Great-circle DX paths** — geodesic lines from your station to active DX beacons
- **Grid square bounding box** — shows the boundaries of your Maidenhead grid square on the map
- Floating map controls: toggle gray line, DX paths, grid square, and recenter

### 📊 Live DX Cluster Spots
- Simulated live spot feed with auto-refresh every 4.5 seconds
- Columns: Time, DX Call, Frequency, Mode, Spotter, SNR, Note
- Filter by band: ALL / 160M / 80M / 40M / 20M / 15M / 10M / 6M
- Filter by mode category: DX Spots / FT8+FT4 / CW
- DXCC entity count displayed

### 🕐 World Clocks
- UTC / Zulu
- New York (ET)
- London (BST/GMT)
- Moscow (MSK)
- Tokyo (JST)
- Sydney (AEST)

### 🌅 Sunrise / Sunset
- Calculated from operator's GPS coordinates (derived from grid square)
- Displays sunrise time, sunset time, and total day length in UTC

### 📝 Quick QSO Logger
- Fields: Callsign, Frequency, Mode, RST Sent/Received
- **Mode options** — organized by category:
  - HF Digital: FT8, FT4, RTTY, PSK31, JS8
  - HF Voice / CW: SSB, CW, AM
  - Digital Voice: DMR, D-STAR, C4FM
  - FM
- **Operation Type selector** — N/A, POTA, SOTA, Field Day, or Other
  - "Other" reveals a free-text description field
- Session QSO counter
- Enter key support on all log fields

### 📰 DX Wire Ticker
- Scrolling ticker at the bottom with solar data, DX spots, and propagation notes

### 📱 Responsive Layout
- **Portrait / mobile friendly** — collapses to single-column at ≤ 900px
- **Pinch-to-zoom** enabled on all touch devices
- Toolbar wraps on small screens; less critical table columns hidden on narrow displays
- Extra-compact layout on phones ≤ 480px

---

## Quick Start

No installation or server required. Just open the file in any modern browser:

```bash
# Double-click the file, or from terminal:
open hamclock-white.html       # macOS
xdg-open hamclock-white.html   # Linux
start hamclock-white.html      # Windows
```

Enter your **callsign** and **grid square** in the top banner. The map will center on your location and all coordinate-dependent features will update automatically.

---

## Requirements

| Requirement | Details |
|---|---|
| Browser | Chrome 90+, Firefox 88+, Safari 14+, Edge 90+ |
| Internet | Required for map tiles (NatGeo) and Google Fonts; core functionality works offline |
| Server | None — runs as a local HTML file |
| Dependencies | Leaflet.js 1.9.4 (loaded from CDN), Google Fonts (loaded from CDN) |

---

## Technical Details

### Grid Square → GPS Conversion
Implements the full Maidenhead Locator System:
- **2-char** (e.g. `FN`) → ±100 km precision
- **4-char** (e.g. `FN31`) → ±5 km precision
- **6-char** (e.g. `FN31pr`) → ±500 m precision
- **8-char** (e.g. `FN31pr48`) → ±50 m precision

### Map
- Tile provider: Esri / National Geographic (`NatGeo_World_Map`)
- Library: Leaflet.js 1.9.4
- Gray-line terminator calculated from solar declination and current UTC time
- DX paths use true great-circle (geodesic) interpolation

### Solar Data
Solar indices (SFI, SSN, K, A, X-ray, Aurora) are simulated on page load for demonstration. To connect live data, replace the `SOLAR` constant in the JavaScript with calls to a real space weather API such as:
- [NOAA Space Weather](https://services.swpc.noaa.gov/json/)
- [HamQSL Solar Widget](https://www.hamqsl.com/solar.html)
- [DXView Propagation API](https://dxview.com)

### Band Conditions
Propagation quality is computed from SFI, K-index, and time of day using simplified ionospheric modeling. For production use, replace with data from [VOACAP](https://www.voacap.com/) or [NOAA SWPC](https://www.swpc.noaa.gov/).

---

## Customization

All colors, fonts, and layout are driven by CSS custom properties in the `:root` block at the top of the `<style>` section. To change the accent color, font sizes, or panel spacing, edit those variables — everything else updates automatically.

To add your own grid square as the default, find this line in the JavaScript:

```javascript
onGridChange(document.getElementById('gridInput').value);
```

And change the input's `value` attribute in the HTML:

```html
<input ... id="gridInput" value="FN31pr" ...>
```

---

## License

© 2026 W7CTY · All Rights Reserved

Personal and non-commercial use permitted. Please credit W7CTY and link back to the original project if you share or adapt this work.

---

## Contact

**W7CTY**
📧 [w7cty@outlook.com](mailto:w7cty@outlook.com)

*73 de W7CTY — Good DX!*
