# HamClock Advanced v3.0.1

**Amateur Radio Operations Center** — by W7CTY

A full-featured ham radio dashboard: live PSKReporter DX paths, HF band conditions, solar/space weather, an interactive propagation map, DX cluster spots, world clocks, and a QSO logger with QRZ upload. Runs in any browser, or as a native Linux app, or on Windows.

-----

## Downloads

|Asset                                     |Platform                  |What’s inside                                                                          |
|------------------------------------------|--------------------------|---------------------------------------------------------------------------------------|
|**HamClockAdvanced-Linux-v3.0.1.tar.gz**  |All Linux distros         |Fedora self-extracting installer, Flatpak, universal installer, browser HTML, PDF guide|
|**HamClockAdvanced-Windows-v3.0.1.tar.gz**|Windows 10/11             |HTML app, Install.bat, Launch.bat, Uninstall.bat, PDF guide                            |
|**HamClock-Fedora-Update-v3.0.1.tar.gz**  |Fedora (existing installs)|Self-extracting update script                                                          |

Verify downloads against `SHA256SUMS.txt`:

```bash
sha256sum -c SHA256SUMS.txt
```

-----

## Quick Start

### Linux

```bash
tar -xzf HamClockAdvanced-Linux-v3.0.1.tar.gz
cd HamClockAdvanced-Linux-v3.0.1
# Fedora (recommended):
chmod +x fedora/install-hamclock-advanced.sh && ./fedora/install-hamclock-advanced.sh
# Any distro:
cd universal && tar -xzf hamclock-advanced-linux-v3.0.1.tar.gz && cd hamclock-advanced-linux && ./install.sh
# Or just open browser/HamClockAdvanced.html
```

### Windows

Extract the archive, then double-click **HamClockAdvanced.html** to run immediately, or right-click **Install.bat → Run as administrator** for a Desktop shortcut and Start Menu entry.

### Fedora — updating an earlier install

```bash
tar -xzf HamClock-Fedora-Update-v3.0.1.tar.gz
cd hamclock-update-final2
chmod +x install-hamclock-advanced.sh && ./install-hamclock-advanced.sh
```

-----

## What’s New in v3.0.1

- **Live PSKReporter DX paths** — great-circle paths to stations that heard your callsign, refreshed every 5 minutes
- **No activity = no paths** — the map stays clean when there are no recent reports for your callsign
- **Radio antenna (Yagi) icon** in the banner
- **☰ MENU button** (red border, gold text) replaces the old gear icon, in its own row so it never overlaps the callsign/grid fields
- **Ticker 75% taller**, centered, always bright gold on black with a red border in both light and dark mode
- **Version shown in footer**

## Security Hardening

- Content-Security-Policy added — restricts scripts, images, and network connections to known origins
- All user inputs (callsign, grid, URL parameters) sanitized with strict allowlists; XSS-safe DOM construction throughout
- QRZ Logbook API calls over HTTPS only
- Shell installers use `set -euo pipefail`; launcher validates the `HAMCLOCK_DATA` path against traversal

-----

## Features

- HF band conditions 160m–6m, day **and** night quality always visible
- Solar indices: SFI, SSN, K-index, A-index, X-ray, Aurora
- Interactive National Geographic propagation map with gray-line terminator
- DX cluster spots (up to 25) with band and mode filtering
- World clocks: UTC + local (auto from grid) plus 6 user-selectable slots
- QSO logger: FT8/FT4, SSB, CW, DMR, D-STAR, C4FM, FM, RTTY, PSK31; POTA/SOTA/Field Day tags
- QRZ Logbook API upload
- Font size 100–200%, expandable map, dark/light theme

-----

## Requirements

- **Browser:** any modern browser (Chrome, Edge, Firefox, Safari)
- **Linux native:** python3, python3-gobject, gtk4, libadwaita, webkitgtk6.0 (installed automatically)
- **Internet:** required for map tiles and PSKReporter live data

-----

© 2026 W7CTY · [w7cty@outlook.com](mailto:w7cty@outlook.com) · *73 de W7CTY — Good DX!*