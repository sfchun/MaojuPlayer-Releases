<h1 align="center">
  <img src="docs/logo.png" alt="MaojuPlayer Logo" width="150">
  <br>
  MaojuPlayer
</h1>

<p align="center">
  <strong>A free, cross-platform, audiophile-grade music player written in Rust.</strong><br>
  Designed with a highly configurable user interface and an uncompromising audio engine.
</p>

## 📥 Downloads

MaojuPlayer is free to use. Download the latest version from the [Releases](../../releases/latest) page. See [CHANGELOG.md](CHANGELOG.md) for what changed in each version.

MaojuPlayer can tell you when a new version is available (**Help → About**). It never downloads or installs an update itself: to update, download the new release here.

| Platform | Build | Status |
|---|---|---|
| **macOS** | ARM64 (Apple Silicon) | Tested on Apple Silicon M4 |
| **Windows** | x64 | Tested on Windows 11 |
| **Linux** | x64 | Tested on Ubuntu 26.04 |
| **Linux** | ARM64 | Experimental: cross-compiled, not tested |

Every release includes a `SHA256SUMS` file. To check a download:

```sh
shasum -a 256 -c SHA256SUMS --ignore-missing      # macOS
sha256sum -c SHA256SUMS --ignore-missing          # Linux
```

On Windows (PowerShell): `Get-FileHash .\<file> -Algorithm SHA256`, then compare the result with the matching line in `SHA256SUMS`.

This repository is the distribution point for official MaojuPlayer releases. MaojuPlayer is closed-source: releases contain the application only, not its source code.

### System requirements

* **macOS:** macOS 14 (Sonoma) or later, on a Mac with Apple Silicon (M1 or later). Intel Macs are not supported.
* **Windows:** Windows 10 or 11, 64-bit (x64), with Microsoft's Visual C++ Redistributable installed (see below) and a graphics card whose driver supports DirectX 12.
* **Linux:** a 64-bit, glibc-based distribution (x64; the ARM64 build is experimental and cannot play WavPack files) with an X11 or Wayland desktop, a graphics driver with Vulkan or OpenGL support, and the ALSA library (`libasound2`, present on almost every desktop). File dialogs use your desktop's file-chooser portal (`xdg-desktop-portal`) or, without it, `zenity`. To add SMB shares from inside the app (**File → Add SMB/UNC path...**), install `gio` and the GVFS SMB backend (`gvfs-backends` on Debian/Ubuntu, `gvfs-smb` on Fedora/Arch; often already installed on GNOME-based desktops); shares you mount yourself work with **File → Add Folder...**.

### First launch

* **macOS:** move MaojuPlayer to *Applications* and open it. If macOS says it cannot verify the app, open **System Settings → Privacy & Security**, click **Open Anyway** next to the MaojuPlayer message, then confirm.
* **Windows:** install Microsoft's Visual C++ Redistributable first (see below), then extract the archive and run `maojuplayer.exe`. If SmartScreen shows "Windows protected your PC", click **More info → Run anyway**.
* **Linux:** extract the archive, make the binary executable (`chmod +x maojuplayer`) and run it. Output goes through ALSA, including PipeWire and PulseAudio via their ALSA devices; bit-perfect output uses your DAC's exclusive ALSA device. On a Wayland desktop, dragging files from the file manager into a playlist only works after you turn on **Force X11 backend** in **General → Configuration... → Startup** and restart the app.

### Windows: install the Visual C++ Redistributable first

MaojuPlayer needs Microsoft's C runtime (`VCRUNTIME140.dll`), which many PCs already have. Without it, Windows shows "The code execution cannot proceed because VCRUNTIME140.dll was not found" and MaojuPlayer does not start.

1. Download Microsoft's installer for the latest version: **[vc_redist.x64.exe](https://aka.ms/vc14/vc_redist.x64.exe)** ("Microsoft Visual C++ v14 Redistributable, x64", for Windows 10 / 11). An older installed version can be too old, so install the latest one. Microsoft's download page: [Latest supported Visual C++ Redistributable downloads](https://learn.microsoft.com/cpp/windows/latest-supported-vc-redist).
2. Run it and click **Install** (administrator rights are needed; a restart is rarely asked).
3. Start MaojuPlayer.

Or, in a terminal: `winget install Microsoft.VCRedist.2015+.x64`

Installing it again is harmless: the installer says when a newer or equal version is already present. Windows Update keeps it up to date. Do not uninstall it: MaojuPlayer and other programs need it.

---

## ✨ Features

### 🎛️ Uncompromising Audio Engine
Designed to feed bit-perfect audio directly to high-end chains, including R2R NOS DACs and dedicated headphone amplifiers.
*   **Bit-Perfect Mode:** True exclusive device access (hog mode on macOS, WASAPI exclusive or ASIO on Windows, direct ALSA hardware device on Linux) with sample rate verification.
*   **Broad Format Support:** MP3, FLAC, OGG Vorbis, Opus, WAV, AAC, ALAC, AIFF, native DSD (DSF/DFF) via a custom decoder, and WavPack (via libwavpack; not available in the Linux ARM64 build).
*   **Advanced DSP Chain:**
    *   **10-Band Parametric EQ:** Peak, shelf, and pass filters with click-free coefficient smoothing and 14 built-in presets.
    *   **Headphone Crossfeed:** Faithful libbs2b port (Default, C.Moy, J.Meier) plus custom MaoJu-cf (4 levels) for a natural, speaker-like soundstage.
    *   **Room Correction:** Real-time convolution with impulse responses for room, speaker, or headphone tuning.
    *   **A/B DSP Bypass:** Compare the processed and unprocessed sound instantly (Ctrl/Cmd+D).
*   **DSD Output:** Native DSD (ASIO on Windows, ALSA on Linux), DoP, or conversion to PCM, with an Auto mode that tries Native, then DoP, then PCM.
*   **Resampling & Upsampling:** High-quality sinc resampling when your device needs another sample rate, plus optional ×2, ×4 or ×8 upsampling.
*   **Gapless & Crossfade:** Seamless track transitions with a pre-queued next track, and equal-power blending (configurable 0.5 s–10 s).
*   **Pro-Audio Touches:** TPDF triangular dithering for bit-depth conversion, ReplayGain normalization, A-weighted spectrum analyzer, realtime bitrate, and precise output format / DAC sample rate display.

### 🎨 Highly Configurable Interface
*   **Tile-Based Layout:** Build your own interface from over 20 zone types, with layout presets and layout export/import.
*   **Edit Mode:** Visual layout editing with split, merge, rotate, and drag-and-drop.
*   **Waveform Metadata Overlay:** Five layouts (Classic, Centered, Compact, Stacked, Minimal) drawn over the track waveform with custom typography, dark/light variants, and subtitle-style readability outlines.
*   **Visualizers & Meters:** Waveform, spectrum, spectrogram, oscilloscope, VU and peak meters, LUFS loudness meter (EBU R128), phase meter / goniometer, and the animated Cosmic Visualizer.
*   **Immersive Views:** A compact Mini Player mode (Ctrl/Cmd+M) and a Full-Screen Album Art mode (Ctrl/Cmd+Enter) with auto-hiding transport controls.
*   **Languages:** The interface is translated into more than 90 languages (**General → Configuration... → Language**). Arabic, Hebrew, Persian and Urdu are experimental: right-to-left layout is not supported yet, so text may be left-aligned and mixed right-to-left and Latin text may appear in the wrong order.

### 🌐 Streaming & Network Integration
> ⚠️ **Disclaimer:** Integrations with third-party platforms (including Tidal, Qobuz, and Roon) are provided strictly for user convenience. MaojuPlayer has no official partnership, commercial agreement, or formal certification with these services. These features may change, break, or be removed at any time without notice if upstream systems change. Streaming requires your own subscription to the service.

*   **Tidal & Qobuz:** Browse favorites, playlists, and search directly in the app, plus featured albums on Qobuz. Full DSP chain support for Tidal FLAC and Qobuz streaming up to 24-bit/192 kHz.
*   **Network Audio:** Internet radio (Icecast/Shoutcast) with a searchable Radio Directory and stream favorites, direct audio URLs, and HLS streams with live ICY metadata display.
*   **Roon Integration:** Acts as a Roon control and display extension. Discover a Roon Core, pair, display now-playing, browse your Roon library, and remote control transport/volume (MaojuPlayer is a controller, not a RAAT audio endpoint).

### 📚 Library Management
*   **High-Speed Scanning:** Parallel folder scanning with active file watching.
*   **CUE Sheet Parsing:** Full support for CUE files (including legacy Cyrillic and CJK encodings) with per-track extraction, validation, and stale detection.
*   **Physical Media:** Audio CD playback and ejection via native OS interfaces on macOS, Windows and Linux.
*   **Network Shares:** Add SMB/NAS shares to your library from the app (**File → Add SMB/UNC path...**).
*   **Search:** A Search window for your library and playlists (Ctrl/Cmd+F).
*   **Smart Playlists, Ratings & Favorites:** Rule-based smart playlists, track ratings and favorites, a User Priority Queue, and a Play History.
*   **MusicBrainz Tagging:** Fill in tags and cover art from MusicBrainz and Cover Art Archive, matched with AcoustID audio fingerprints, and review the changes before they are written.
*   **Lyrics:** Synced and plain lyrics from your files' tags, `.lrc` files, LRCLIB and NetEase Cloud Music, with a built-in sync mode to time lyrics yourself.
*   **Scrobbling:** Last.fm and ListenBrainz, with an offline queue that retries automatically.
*   **Media Keys:** Play/pause and track keys plus the system's now-playing controls on macOS, Windows and Linux (MPRIS).
*   **Settings Persistence:** Automatically saves your layout, playlists, preferences, and window geometry.

---

## 🔒 Privacy & network use

MaojuPlayer has no telemetry, no analytics and no account of its own. It connects to other servers only for the features you use and to check for updates:

* **Streaming:** Qobuz and Tidal (their APIs and content servers; signing in opens your browser), Internet radio (the radio-browser.info directory and the stations you play), and any stream URL you enter (web pages are read to find the stream inside).
* **Your network:** network shares (SMB/NAS) you add to your library, and Roon (discovered on your local network).
* **Metadata:** MusicBrainz, Cover Art Archive and AcoustID for auto-tagging (an audio fingerprint of the track is sent to AcoustID), and LRCLIB and NetEase Cloud Music for lyrics (artist, title, album and duration are sent). To find lyrics, MaojuPlayer can also send a track's AcoustID tag to AcoustID, and the artist name to MusicBrainz to look up other spellings of it.
* **Scrobbling:** Last.fm and ListenBrainz, when you enable them.
* **Updates:** at startup (at most once a day) and when you click **Check now**, MaojuPlayer asks GitHub (`api.github.com`) for the latest release. Only your IP address and the app's user agent (`MaojuPlayer/<version> ( https://github.com/sfchun/MaojuPlayer-Releases )`) are sent, and nothing is downloaded. Turn it off with **Check for updates automatically** in **Help → About**.

The same user agent is sent to the radio, metadata, lyrics and scrobbling services. The Qobuz and Tidal sign-in and browsing services see a browser user agent instead; audio and cover downloads from their content servers can carry the MaojuPlayer user agent.

Streaming and scrobbling credentials are kept in your operating system's credential store: macOS Keychain, Windows Credential Manager, or the Linux kernel session keyring (cleared when you log out or restart, so you may need to sign in again). If no credential store is available, they are kept in the settings file, which only your user account can read. Network-share (SMB) logins you choose to remember and the Roon pairing token also go to the credential store.

---

## 🔐 Security

Found a security problem? Please report it privately. See [SECURITY.md](SECURITY.md).

## 🛠️ Support & Bug Reports

MaojuPlayer is actively maintained. To keep support manageable, bug reports and technical support are offered to **monthly GitHub Sponsors**:

1. Choose a monthly tier on the [GitHub Sponsors page](https://github.com/sponsors/sfchun).
2. Monthly sponsorship tiers give you access to the private `MaojuPlayer-Support` repository. One-time sponsorships are a welcome thank-you, but they do not include support access.
3. Open an issue there with one of the forms (bug report, feature request, help request).

## 📄 License

MaojuPlayer is freeware: free to download and use, all rights reserved. See [LICENSE.txt](LICENSE.txt) for the terms.

MaojuPlayer includes open-source components used under their own licences. Their notices are in [THIRD-PARTY-LICENSES.txt](THIRD-PARTY-LICENSES.txt) and are also included in every release download.
