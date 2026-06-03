# HamClock Advanced — v3.1.0

**Amateur Radio Operations Center** by **W7CTY**
Hosted at **https://github.com/W7CTY/HamClock**

A full-featured ham radio dashboard: live PSKReporter DX paths, HF band
conditions, solar/space weather, an interactive National Geographic propagation
map with a full day/night gray line, sun & moon markers, live weather, DX
cluster spots, world clocks, and a QSO logger with QRZ upload. Runs in any
browser, or as a native Linux app, or on Windows.

> Note: This is an independent HTML/GTK4 reimplementation — not the upstream
> HamClock by Elwood Downey (WB0OEW).

---

## Downloads

| File | Platform | Contents |
|---|---|---|
| `HamClockAdvanced-Linux-v3.1.0.tar.gz` | All Linux distros | Fedora installer, Flatpak, Universal, Browser HTML, PDF |
| `HamClockAdvanced-Windows-v3.1.0.tar.gz` | Windows 10/11 | HTML app, Install/Uninstall .bat, PDF |
| `HamClock-Fedora-Update-v3.1.0.tar.gz` | Fedora (existing installs) | Self-extracting installer + PDF |
| `hamclock-public.html` | Any browser | Standalone — open directly, no install |

Verify downloads against `SHA256SUMS.txt`:
```bash
sha256sum -c SHA256SUMS.txt
```

---

## Quick Start

### Linux
```bash
tar -xzf HamClockAdvanced-Linux-v3.1.0.tar.gz
cd HamClockAdvanced-Linux-v3.1.0
# Fedora (recommended):
chmod +x fedora/install-hamclock-advanced.sh && ./fedora/install-hamclock-advanced.sh
# Any distro:
cd universal && tar -xzf hamclock-advanced-linux-v3.1.0.tar.gz
cd hamclock-advanced-linux && chmod +x install.sh && ./install.sh
# Or just open browser/HamClockAdvanced.html
hamclock-advanced
```

### Windows
Extract the archive, then double-click **HamClockAdvanced.html** to run, or
right-click **Install.bat → Run as administrator** for a Desktop shortcut.

### Fedora update (existing install)
```bash
tar -xzf HamClock-Fedora-Update-v3.1.0.tar.gz
cd hamclock-update-final2
chmod +x install-hamclock-advanced.sh && ./install-hamclock-advanced.sh
```

---

## Updating

HamClock Advanced checks GitHub for new releases on launch and shows a banner
when an update is available. To update:

| Method | Command |
|---|---|
| Fedora / RPM / Universal | `hamclock-advanced --update` |
| Flatpak | `flatpak update org.w7cty.HamClockAdvanced` |
| Windows | Download the latest release and run `Install.bat` again |
| Any | Download from https://github.com/W7CTY/HamClock/releases/latest |

The in-app check is read-only — it never downloads or installs anything on its
own. Updates are applied only when you choose to. Disable the check with
`HAMCLOCK_NO_UPDATE_CHECK=1`.

---

## Uninstall

| Method | Command |
|---|---|
| Fedora / RPM / Universal | `hamclock-advanced --uninstall` |
| Fedora self-extracting | `sudo bash /usr/share/hamclock-advanced/uninstall-hamclock.sh` |
| Flatpak | `flatpak uninstall --user org.w7cty.HamClockAdvanced` |
| Universal Linux | `sudo bash /opt/hamclock-advanced/uninstall.sh` |
| Windows | Run `Uninstall.bat` |

---

## Command-Line Options (Linux)

```
hamclock-advanced              Launch the application
hamclock-advanced --update     Check for and install the latest release
hamclock-advanced --uninstall  Remove HamClock Advanced from this system
hamclock-advanced --version    Print version and exit
hamclock-advanced --help       Show help
```

---

## What's New in v3.1.0

- **Full-width day/night gray line** — the terminator is computed for every
  longitude, so it now spans edge to edge with no gaps
- **Night-side shading** — soft translucent fill marks the night hemisphere
  (no hard outline lines)
- **Sun marker** on the daylight side and **Moon marker** (with current phase &
  illumination) at the sub-lunar point on the night side
- **Weather button** — live sky conditions and day/night at the map center, for
  anywhere on Earth, via Open-Meteo (no API key required)
- **Grid square overlay off by default** (toggle on from the map toolbar)
- **Radio-antenna station icon** replaces the old QTH marker
- **USA 250 patriotic theme** — red/white/blue with an American flag and
  "1776–2026 · 250" mark, always on, in both day and night cycles
- **In-app update check** + `--update` / `--uninstall` commands
- **Security hardening** — CSP, sanitized inputs, HTTPS-only APIs (see below)

---

## Features

- HF band conditions 160m–6m, day AND night quality always visible
- Solar indices: SFI, SSN, K-index, A-index, X-ray, Aurora
- Interactive NatGeo propagation map with real-time gray line, sun & moon
- Live weather at any map location (Open-Meteo)
- DX cluster spots (up to 25) with band/mode filtering
- Live PSKReporter paths — stations that heard your callsign, refreshed every 5 min
- World clocks: UTC + local (auto from grid) + 6 user slots
- QSO logger: FT8/FT4, SSB, CW, DMR, D-STAR, C4FM, FM, RTTY, PSK31; POTA/SOTA/Field Day
- QRZ Logbook API upload
- Font size 100–200%, expandable map, dark/light theme

---

## Security

Every release passes a deep pre-publish audit (see `PRE-PUBLISH-CHECKLIST.md`):
- Content-Security-Policy restricting script/connect/image origins
- All user input (callsign, grid, URL params) sanitized; XSS-safe DOM throughout
- HTTPS-only external APIs (PSKReporter, QRZ, Open-Meteo, solar data)
- In-app update check is read-only; no silent privileged installs
- Shell installers use `set -euo pipefail` and valid `chmod` octal modes
- base64 install payloads verified to decode to the expected files
- Launcher validates the `HAMCLOCK_DATA` path against traversal

---

## Requirements

- **Browser version:** any modern browser (Chrome, Edge, Firefox, Safari)
- **Linux native:** python3, python3-gobject, gtk4, libadwaita, webkitgtk6.0 (auto-installed)
- **Windows:** Windows 10 or 11 with any modern browser
- **Internet:** required for map tiles, weather, and live PSKReporter / solar data

---

© 2026 W7CTY · w7cty@outlook.com · github.com/W7CTY/HamClock · *73 de W7CTY — Good DX!*
