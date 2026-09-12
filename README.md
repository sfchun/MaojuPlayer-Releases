<h1 align="center">
  <!-- Note: Update path to your cat listening to music logo -->
  <img src="docs/logo.png" alt="MaojuPlayer Logo" width="150">
  <br>
  MaojuPlayer
</h1>

<p align="center">
  <strong>A free, cross-platform, audiophile-grade music player written in Rust.</strong><br>
  Designed with a highly configurable user interface and an uncompromising audio engine.
</p>

## 📥 Downloads

MaojuPlayer is free to use. Pre-compiled binaries are available in the [Releases](../../releases) tab.

*   **macOS** (ARM64, compiled and tested on Apple Silicon M4)
*   **Windows** (x64, compiled and tested on Windows11)
*   **Linux** (x64, compiled and tested on Ubuntu 26.04)
*   **Linux** (ARM64, cross-compiled, not tested)

*Note: The source code is currently closed, and this repository serves strictly as a distribution point for official releases.*

---

## ✨ Features

### 🎛️ Uncompromising Audio Engine
Designed to feed bit-perfect audio directly to high-end chains, including R2R NOS DACs and dedicated headphone amplifiers.
*   **Bit-Perfect Mode:** True exclusive device access (hog mode) with sample rate verification.
*   **Broad Format Support:** MP3, FLAC, OGG, WAV, AAC, ALAC, AIFF (via Symphonia), native DSD (DSF/DFF) via a custom decoder, and WavPack (via libwavpack FFI).
*   **Advanced DSP Chain:** 
    *   **10-Band Parametric EQ:** Peak, shelf, and pass filters with click-free coefficient smoothing and 14 built-in presets.
    *   **Headphone Crossfeed:** Faithful libbs2b 3.1.0 port (Default, C.Moy, J.Meier) plus custom MaoJu-cf (4 levels) for a natural, speaker-like soundstage.
    *   **Room Correction:** Real-time convolution with impulse responses for room, speaker, or headphone tuning.
*   **Gapless & Crossfade:** Seamless track transitions with pre-queued next track, and equal-power blending (configurable 0.5s–10s).
*   **Pro-Audio Touches:** Proper TPDF triangular dithering for bit-depth conversion, ReplayGain normalization, A-Weighted spectrum analyzer, realtime bitrate, and precise output format DAC sample rate display.

### 🎨 Highly Configurable Interface
*   **Tile-Based Layout:** Build your perfect customized interface using over 20 unique zone types.
*   **Edit Mode:** Visual layout editing with split, merge, rotate, and drag-and-drop mechanics.
*   **Waveform Metadata Overlay:** Five layouts (Classic, Centered, Compact, Stacked, Minimal) drawn directly over the track waveform with custom typography, dark/light variants, and subtitle-style readability outlines. 
*   **Immersive Views:** A compact Mini Player mode (Ctrl/Cmd+M) and a Full-Screen Album Art mode featuring auto-hiding transport controls.

### 🌐 Streaming & Network Integration
> ⚠️ **Disclaimer:** Integrations with third-party platforms (including Tidal, Qobuz, and Roon) are provided strictly for user convenience. MaojuPlayer has no official partnership, commercial agreement, or formal certification with these services. Consequently, these features may change, break, or be removed at any time without notice if upstream systems are updated.

*   **Tidal & Qobuz:** Browse favorites, playlists, featured albums, and search directly in the app. Full DSP chain support for Tidal FLAC and Qobuz streaming up to 24-bit/192kHz.
*   **Network Audio:** Support for Internet radio (Icecast/Shoutcast), direct audio URLs, and HLS streams with live ICY metadata display.
*   **Roon Integration:** Acts as a Roon control and display extension. Discover a Roon Core, pair, display now-playing, and remote control transport/volume (Note: MaojuPlayer acts as a controller, not a RAAT audio endpoint).

### 📚 Library Management
*   **High-Speed Scanning:** Parallel folder scanning with resumable checkpoints and active file watching.
*   **CUE Sheet Parsing:** Full support for CUE files with per-track extraction, validation, and stale detection.
*   **Physical Media:** Audio CD playback and ejection support via native OS APIs (GVFS on Linux, diskutil on macOS, Windows API).
*   **Settings Persistence:** Automatically saves your layout, playlists, preferences, and window geometry.

---

## 🛠️ Support & Bug Reports

MaojuPlayer is actively maintained, but to manage the volume of support requests, bug reporting and technical support are gated via **GitHub Sponsors**. 

If you find the player valuable and want to report a bug, request a feature, or receive direct support:
1. Sponsor the project via the [GitHub Sponsors page](https://github.com/sponsors/sfchun).
2. Upon sponsoring, you will automatically be granted access to the private `MaojuPlayer-Support` repository.
3. Open an issue in the support repository.

## 📄 License
MaojuPlayer is distributed as freeware. All rights reserved.
