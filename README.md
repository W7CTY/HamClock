# HamClock Advanced — v3.1.0

**Amateur Radio Operations Center** by **W7CTY**
🔗 https://github.com/W7CTY/HamClock

A full-featured ham radio dashboard for the browser, Linux desktop, and Windows. Features live PSKReporter DX paths, HF band conditions, solar/space weather, an interactive National Geographic propagation map with a full day/night gray line, sun & moon markers, live weather, DX cluster spots, world clocks, and a QSO logger with QRZ upload.

> **Note:** This is an independent HTML/GTK4 reimplementation — not the upstream HamClock by Elwood Downey (WB0OEW).

---

## Features

- HF band conditions 160m–6m, day and night quality always visible
- Solar indices: SFI, SSN, K-index, A-index, X-ray, Aurora
- Interactive NatGeo propagation map with real-time gray line, sun & moon markers
- Live weather at any map location via Open-Meteo (no API key required)
- DX cluster spots (up to 25) with band/mode filtering
- Live PSKReporter paths — stations that heard your callsign, refreshed every 5 min
- World clocks: UTC + local (auto from grid) + 6 user slots
- QSO logger: FT8/FT4, SSB, CW, DMR, D-STAR, C4FM, FM, RTTY, PSK31; POTA/SOTA/Field Day
- QRZ Logbook API upload
- Font size 100–200%, expandable map, dark/light theme

---

## Downloads

| File | Platform | Contents |
|---|---|---|
| `HamClockAdvanced-Linux-v3.1.0.tar.gz` | All Linux distros | Fedora installer, Flatpak, Universal, Browser HTML, PDF |
| `HamClockAdvanced-Windows-v3.1.0.tar.gz` | Windows 10/11 | HTML app, Install/Uninstall .bat, PDF |
| `HamClock-Fedora-Update-v3.1.0.tar.gz` | Fedora (existing installs) | Self-extracting installer + PDF |
| `hamclock-public.html` | Any browser | Standalone — open directly, no install needed |

Verify downloads against `SHA256SUMS.txt`:
```bash
sha256sum -c SHA256SUMS.txt
```

---

## Quick Start

### Browser
Open `hamclock-public.html` directly in any modern browser — no install required.

### Linux
```bash
tar -xzf HamClockAdvanced-Linux-v3.1.0.tar.gz
cd HamClockAdvanced-Linux-v3.1.0

# Fedora (recommended):
chmod +x fedora/install-hamclock-advanced.sh && ./fedora/install-hamclock-advanced.sh

# Any distro (universal installer):
cd universal && tar -xzf hamclock-advanced-linux-v3.1.0.tar.gz
cd hamclock-advanced-linux && chmod +x install.sh && ./install.sh

hamclock-advanced
```

### Windows
Extract the archive, then double-click **HamClockAdvanced.html** to run, or right-click **Install.bat → Run as administrator** for a Desktop shortcut.

### Fedora update (existing install)
```bash
tar -xzf HamClock-Fedora-Update-v3.1.0.tar.gz
cd hamclock-update-final2
chmod +x install-hamclock-advanced.sh && ./install-hamclock-advanced.sh
```

---

## Updating

HamClock Advanced checks GitHub for new releases on launch and shows a banner when an update is available.

| Method | Command |
|---|---|
| Fedora / RPM / Universal | `hamclock-advanced --update` |
| Flatpak | `flatpak update org.w7cty.HamClockAdvanced` |
| Windows | Download the latest release and run `Install.bat` again |
| Any | https://github.com/W7CTY/HamClock/releases/latest |

The in-app check is read-only — it never downloads or installs anything automatically. Disable with `HAMCLOCK_NO_UPDATE_CHECK=1`.

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

## Requirements

| Platform | Requirements |
|---|---|
| Browser | Any modern browser (Chrome, Edge, Firefox, Safari) |
| Linux native | python3, python3-gobject, gtk4, libadwaita, webkitgtk6.0 (auto-installed) |
| Windows | Windows 10 or 11 with any modern browser |
| Internet | Required for map tiles, weather, and live PSKReporter / solar data |

---

## Security

Every release passes a full pre-publish audit (`PRE-PUBLISH-CHECKLIST.md`):

- Content-Security-Policy restricting script/connect/image origins
- All user input (callsign, grid, URL params) sanitized; XSS-safe DOM throughout
- HTTPS-only external APIs (PSKReporter, QRZ, Open-Meteo, solar data)
- In-app update check is read-only; no silent privileged installs
- Shell installers use `set -euo pipefail` and valid `chmod` octal modes
- base64 install payloads verified to decode to expected files
- Launcher validates the `HAMCLOCK_DATA` path against traversal

---

## What's New in v3.1.0

- **Full-width day/night gray line** — terminator computed for every longitude, spanning edge to edge
- **Night-side shading** — soft translucent fill marks the night hemisphere
- **Sun & Moon markers** — sun on daylight side, moon with phase & illumination on night side
- **Weather button** — live sky conditions at any map center via Open-Meteo
- **Grid square overlay off by default** (toggle on from map toolbar)
- **Radio-antenna station icon** replaces old QTH marker
- **USA 250 patriotic theme** — red/white/blue with American flag and "1776–2026 · 250" mark
- **In-app update check** + `--update` / `--uninstall` commands
- **Security hardening** — CSP, sanitized inputs, HTTPS-only APIs

---

## License

Apache License 2.0 — see [LICENSE](LICENSE)

---

© 2026 W7CTY · w7cty@outlook.com · github.com/W7CTY/HamClock · *73 de W7CTY — Good DX!*

