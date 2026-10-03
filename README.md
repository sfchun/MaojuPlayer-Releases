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

MaojuPlayer is free to use. Download the latest version from the [Releases](../../releases/latest) page.

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

### First launch

* **macOS:** move MaojuPlayer to *Applications* and open it. If macOS says it cannot verify the app, open **System Settings → Privacy & Security**, click **Open Anyway** next to the MaojuPlayer message, then confirm.
* **Windows:** extract the archive and run `maojuplayer.exe`. If SmartScreen shows "Windows protected your PC", click **More info → Run anyway**.
* **Linux:** extract the archive, make the binary executable (`chmod +x maojuplayer`) and run it. Output goes through ALSA, including PipeWire and PulseAudio via their ALSA devices; bit-perfect output uses your DAC's exclusive ALSA device.

---

## ✨ Features

### 🎛️ Uncompromising Audio Engine
Designed to feed bit-perfect audio directly to high-end chains, including R2R NOS DACs and dedicated headphone amplifiers.
*   **Bit-Perfect Mode:** True exclusive device access (hog mode) with sample rate verification.
*   **Broad Format Support:** MP3, FLAC, OGG Vorbis, Opus, WAV, AAC, ALAC, AIFF, native DSD (DSF/DFF) via a custom decoder, and WavPack (via libwavpack; not available in the Linux ARM64 build).
*   **Advanced DSP Chain:**
    *   **10-Band Parametric EQ:** Peak, shelf, and pass filters with click-free coefficient smoothing and 14 built-in presets.
    *   **Headphone Crossfeed:** Faithful libbs2b port (Default, C.Moy, J.Meier) plus custom MaoJu-cf (4 levels) for a natural, speaker-like soundstage.
    *   **Room Correction:** Real-time convolution with impulse responses for room, speaker, or headphone tuning.
*   **Gapless & Crossfade:** Seamless track transitions with a pre-queued next track, and equal-power blending (configurable 0.5 s–10 s).
*   **Pro-Audio Touches:** TPDF triangular dithering for bit-depth conversion, ReplayGain normalization, A-weighted spectrum analyzer, realtime bitrate, and precise output format / DAC sample rate display.

### 🎨 Highly Configurable Interface
*   **Tile-Based Layout:** Build your own interface from over 20 zone types.
*   **Edit Mode:** Visual layout editing with split, merge, rotate, and drag-and-drop.
*   **Waveform Metadata Overlay:** Five layouts (Classic, Centered, Compact, Stacked, Minimal) drawn over the track waveform with custom typography, dark/light variants, and subtitle-style readability outlines.
*   **Immersive Views:** A compact Mini Player mode (Ctrl/Cmd+M) and a Full-Screen Album Art mode with auto-hiding transport controls.
*   **Languages:** The interface is translated into more than 90 languages.

### 🌐 Streaming & Network Integration
> ⚠️ **Disclaimer:** Integrations with third-party platforms (including Tidal, Qobuz, and Roon) are provided strictly for user convenience. MaojuPlayer has no official partnership, commercial agreement, or formal certification with these services. These features may change, break, or be removed at any time without notice if upstream systems change. Streaming requires your own subscription to the service.

*   **Tidal & Qobuz:** Browse favorites, playlists, featured albums, and search directly in the app. Full DSP chain support for Tidal FLAC and Qobuz streaming up to 24-bit/192 kHz.
*   **Network Audio:** Internet radio (Icecast/Shoutcast), direct audio URLs, and HLS streams with live ICY metadata display.
*   **Roon Integration:** Acts as a Roon control and display extension. Discover a Roon Core, pair, display now-playing, and remote control transport/volume (MaojuPlayer is a controller, not a RAAT audio endpoint).

### 📚 Library Management
*   **High-Speed Scanning:** Parallel folder scanning with active file watching.
*   **CUE Sheet Parsing:** Full support for CUE files (including legacy Cyrillic and CJK encodings) with per-track extraction, validation, and stale detection.
*   **Physical Media:** Audio CD playback and ejection via native OS APIs (GVFS on Linux, diskutil on macOS, Windows API).
*   **Settings Persistence:** Automatically saves your layout, playlists, preferences, and window geometry.

---

## 🔒 Privacy & network use

MaojuPlayer has no telemetry, no analytics, no update check and no account of its own. It connects to other servers only for the features you use:

* **Streaming:** Qobuz and Tidal (their APIs and content servers; signing in opens your browser), Internet radio (the radio-browser.info directory and the stations you play), and any stream URL you enter (web pages are read to find the stream inside).
* **Your network:** network shares (SMB/NAS) you add to your library, and Roon (discovered on your local network).
* **Metadata:** MusicBrainz, Cover Art Archive and AcoustID for auto-tagging (an audio fingerprint of the track is sent to AcoustID), and LRCLIB and NetEase Cloud Music for lyrics (artist, title, album and duration are sent).
* **Scrobbling:** Last.fm and ListenBrainz, when you enable them.

Streaming and scrobbling credentials are kept in your operating system's credential store: macOS Keychain, Windows Credential Manager, or the Linux kernel session keyring (cleared when you log out or restart, so you may need to sign in again). If no credential store is available, they are kept in the settings file, which only your user account can read.

---

## 🔐 Security

Found a security problem? Please report it privately. See [SECURITY.md](SECURITY.md).

## 🛠️ Support & Bug Reports

MaojuPlayer is actively maintained. To keep support manageable, bug reports and technical support are offered to **GitHub Sponsors**:

1. Sponsor the project on the [GitHub Sponsors page](https://github.com/sponsors/sfchun).
2. Sponsoring grants you access to the private `MaojuPlayer-Support` repository.
3. Open an issue there with one of the forms (bug report, feature request, help request).

## 📄 License

MaojuPlayer is freeware: free to download and use, all rights reserved. See [LICENSE.txt](LICENSE.txt) for the terms.

MaojuPlayer includes open-source components used under their own licences. Their notices are in [THIRD-PARTY-LICENSES.txt](THIRD-PARTY-LICENSES.txt) and are also included in every release download.
