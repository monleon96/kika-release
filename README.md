<p align="center">
  <img src="logo.png" alt="KIKA" width="300">
</p>

<p align="center">
  <a href="../../releases/latest"><img src="https://img.shields.io/github/v/release/monleon96/kika-release?label=KIKA%20App&color=blue" alt="App Version"></a>
  <a href="https://pypi.org/project/kika-nd/"><img src="https://img.shields.io/pypi/v/kika-nd?label=kika-nd&color=blue" alt="PyPI Version"></a>
  <img src="https://img.shields.io/badge/status-beta-orange" alt="Beta">
</p>

<p align="center">
  An all-in-one desktop toolkit for nuclear engineers. Explore and visualize nuclear data, build simulation inputs, and run sensitivity and uncertainty analyses.
</p>

## Download

Go to the [Releases](../../releases/latest) page and download the installer for your platform:

| Platform | File | Notes |
|----------|------|-------|
| **Windows** | `KIKA_x.x.x_x64-setup.exe` | Run the installer and follow the setup wizard |
| **Linux** | `KIKA_x.x.x_amd64.AppImage` | Make executable and run (see below) |
| **macOS** | `KIKA_x.x.x_aarch64.dmg` | Apple Silicon (M1/M2/M3/M4) |

## Installation

### Windows

1. Download the `.exe` installer
2. Run the installer and follow the setup wizard
3. Launch KIKA from the Start Menu or desktop shortcut

### Linux

1. Download the `.AppImage` file
2. Make it executable and run:
   ```bash
   chmod +x KIKA_*.AppImage
   ./KIKA_*.AppImage
   ```

**System requirements** — the following libraries must be installed:

```bash
# Debian / Ubuntu (23.04+)
sudo apt install libgtk-3-0 libwebkit2gtk-4.1-0 librsvg2-2 libsoup-3.0-0 libjavascriptcoregtk-4.1-0
```

> **Known issue — Ubuntu 22.04 and older distributions**
>
> KIKA requires `libwebkit2gtk-4.1` and `libsoup-3.0`, which are **not available** in Ubuntu 22.04 LTS or older releases (they ship the older `4.0` / `2.4` versions). You need **Ubuntu 23.04+**, Fedora 38+, or another distribution that packages these libraries. There is currently no workaround for older distributions.

### macOS

1. Download the `.dmg` file
2. Open the DMG and drag KIKA to your Applications folder
3. On first launch, macOS Gatekeeper may block the app. Go to **System Settings > Privacy & Security** and click **Open Anyway**

## Corporate Proxy

If your network requires an HTTP proxy (common in corporate environments), KIKA may fail to connect on launch. You can work around this by starting KIKA from a script that sets the proxy environment variables.

### Windows

Create a file called `kika-proxy.bat` and run it instead of the shortcut:

```bat
@echo off

rem === 1) Configure proxy for this session ===
rem Replace the values below with your actual proxy details
set HTTP_PROXY=http://USERNAME:PASSWORD@proxy.example.com:8080
set HTTPS_PROXY=%HTTP_PROXY%
set http_proxy=%HTTP_PROXY%
set https_proxy=%HTTP_PROXY%

rem === 2) Hosts that should bypass the proxy (comma-separated) ===
set NO_PROXY=localhost,127.0.0.1
set no_proxy=%NO_PROXY%

rem === 3) Launch KIKA ===
rem Default install path — adjust if you installed elsewhere
"%LOCALAPPDATA%\KIKA\KIKA.exe"
```

### Linux / macOS

```bash
#!/bin/bash

export HTTP_PROXY="http://USERNAME:PASSWORD@proxy.example.com:8080"
export HTTPS_PROXY="$HTTP_PROXY"
export NO_PROXY="localhost,127.0.0.1"

# Adjust the path to your KIKA installation
/path/to/KIKA.AppImage
```

Make it executable with `chmod +x kika-proxy.sh` and run it instead of launching KIKA directly.

## Auto-Update

KIKA checks for updates automatically on launch. When a new version is available you will be prompted to download and install it.

## Built on the kika Python Library

This desktop app is built on top of [**kika**](https://github.com/monleon96/kika), an open-source Python toolkit for nuclear data analysis, Monte Carlo simulation support, and uncertainty quantification. Almost everything available in the app can also be accessed programmatically through the library.

If you'd like to contribute, head over to the Python library repo. You can install it with:

```bash
pip install kika-nd
```

Or by cloning the repository:

```bash
git clone https://github.com/monleon96/kika.git
cd kika
pip install -e .
```

> **Note:** The PyPI package is called `kika-nd`, but you import it as `import kika`.

## Links

- [kika Python library](https://github.com/monleon96/kika)
- [Report an issue](../../issues)
