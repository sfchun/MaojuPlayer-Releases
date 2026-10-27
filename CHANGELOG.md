# Changelog

All notable changes to MaojuPlayer are listed here, newest first.
Each version matches a release tag (`vX.Y.Z`) on the [Releases](../../releases) page.

## v3.6.0 — first public release

Date: Unreleased

This is the first public release of MaojuPlayer. It lists the main features you get today.

### 🎛️ Audio engine

* **Bit Perfect mode:** exclusive access to your DAC (hog mode on macOS, WASAPI exclusive or ASIO on Windows, an exclusive ALSA device on Linux). The Bit Perfect button shows green when the signal is untouched, amber when a setting you chose changes it, and red when something outside MaojuPlayer breaks the path.
* **Gapless playback** with the next track prepared in advance, or **Crossfade** (equal-power, 0.5 s to 10 s). Crossfade can keep the device rate for seamless transitions. Crossfade is not applied in Bit Perfect mode.
* **Pre-buffering to RAM:** optionally decode whole tracks into memory before playback, with a maximum RAM setting.
* **10-band parametric EQ:** peak, shelf and pass filters, 14 built-in presets plus your own presets, and a pre-amp.
* **Headphone crossfeed:** BS2B (Default, C.Moy, J.Meier) and MaoJu-cf 1 to 4.
* **Room Correction:** real-time convolution with impulse responses for room, speaker or headphone correction.
* **ReplayGain:** Off, Track, Album or Smart (track gain when shuffling, album gain otherwise), separate pre-amps for tracks with and without ReplayGain info, and a built-in scanner (EBU R128) that writes ReplayGain tags to your files.
* **Volume:** software volume (logarithmic or linear), the device's own hardware volume (stays bit-perfect), or fixed at 100 %. Also channel balance, inter-sample peak protection (Off for R2R / NOS DACs, Auto for oversampling DACs), resampling quality (Fast, Normal, High) and TPDF dithering.
* **Audio Profiles:** save and load snapshots of your audio settings.
* **A/B DSP bypass** (Ctrl/Cmd+D) and a **Signal Chain** panel that shows what processes the sound.

### 🎵 Formats

* **Local files:** FLAC, MP3, AAC and ALAC (M4A / MP4), Ogg Vorbis, Opus, WAV, AIFF / AIFC and WavPack.
* **DSD (DSF and DFF):** Auto, Native DSD, DoP (DSD over PCM, up to DSD256) or PCM conversion. A one-time listening check asks whether your DAC plays DoP or native DSD cleanly and remembers the answer per device.
* **CUE sheets:** album images split into tracks, with legacy text encodings (for example Cyrillic and CJK) detected.
* **Audio CD:** play, browse and eject discs, with an optional LED-style CD display (12 styles).
* **Playlist files:** load M3U, M3U8 and PLS; save as M3U8 or PLS.
* **Internet streams:** Icecast / Shoutcast radio with live track titles, direct audio URLs and HLS streams.

### 🌐 Streaming & services

Streaming requires your own subscription to the service. MaojuPlayer has no partnership with these services.

* **Qobuz:** sign in through your browser; browse favorites, playlists, featured albums and search; play up to 24-bit / 192 kHz through the full DSP chain.
* **Tidal:** sign in by entering a short code at link.tidal.com; browse favorites, playlists and search; lossless FLAC playback through the full DSP chain.
* **Radio Directory:** find stations from radio-browser.info by country, genre or search, and keep your favorite streams.
* **Roon:** control and display extension. Find a Roon Core, pair, show now playing, control transport and volume, and browse your Roon library.
* **MusicBrainz tagging:** "Tag/Art with MusicBrainz" matches tracks (with an AcoustID audio fingerprint), fetches cover art from the Cover Art Archive, and lets you review the changes before files are written.
* **Scrobbling:** Last.fm and ListenBrainz. Scrobbles are queued and retried when the network is back. You can also "Love" tracks on Last.fm.
* Streaming and scrobbling credentials are kept in your operating system's credential store.

### 📚 Library & playlists

* **Fast library scan:** parallel scanning that skips unchanged files, and folder watching that picks up changes.
* **Network shares:** File → Add SMB/UNC path... mounts `smb://server/share` or `\\server\share` for you and asks for a login when needed.
* **Search window** (Ctrl/Cmd+F): search the library or playlists, group the results, play them, add them to a playlist or the Priority Queue.
* **Smart playlists:** rules on tags, file details, rating, favorite, play count and more, with a limit and a sort order. Playlists can also be generated from favorites and ratings.
* **Ratings, favorites, play count and last played**, shown as playlist columns.
* **User Priority Queue** and **Play History** panels.
* Playlist tabs with colors, drag-and-drop of files and folders, grayed rows for unavailable files, and "Clear deleted files".
* **Properties** (Cmd+I on macOS, Alt+Enter on Windows and Linux): edit tags of one or many tracks, artwork (front, back, artist) and ReplayGain values.
* **Convert to…** (right-click tracks or albums): lossless conversion to ALAC (.m4a), FLAC, WAV or AIFF. Bit depth and sample rate stay exactly as in the source, every file is read back and checked after writing, and tags and cover art are kept (anything that can't be kept is listed before you start). Files are saved next to the source or in a folder you choose, with file names from presets or your own pattern; existing files are only replaced if you allow it, and a source file is never replaced.
* **Databases menu:** export and import the metadata and lyrics databases.
* **Resume playback** where you left off, and a **sleep timer**.

### 🎤 Lyrics

* Synced and plain lyrics from embedded tags, `.lrc` files, LRCLIB and NetEase Cloud Music.
* Better matching: optional AcoustID lookup for clean metadata, and an option to also search under the artist's other names (MusicBrainz).
* **Sync mode:** tap each line to time it, then fix single lines, pin lines, even out drift, undo / redo, replay and loop.
* **Offset:** scroll over the offset to move lyrics earlier or later (0.1 s per notch, 0.5 s with Shift), then click Keep to save it.
* Paste or edit lyrics, import and export lyrics, and accept or reject the lyrics text and its timing.
* Display presets, color palettes, and layout and typography settings.

### 🎨 Interface

* **Tile-based layout** with more than 20 zone types, **Edit Layout** (F2) with split, merge, rotate and drag-and-drop, Lock Layout, layout presets, and layout export / import.
* **Visualizers:** waveform (several styles, A-B loop, track info shown over the waveform, five layouts), spectrum (optional A-weighting), spectrogram, VU meter, peak meter, LUFS meter, phase meter, oscilloscope and the Cosmic Visualizer.
* **Visual Tones:** one color theme for every visualizer, with presets (Studio, Vinyl Warm, Neon Lab, Paper Light, Pure Mono), plus per-window transparency.
* **Mini Player** (Ctrl/Cmd+M) and **full-screen album art** (Ctrl/Cmd+Enter) with auto-hiding transport controls.
* **Keyboard Shortcuts** overlay (F1).
* Media keys and the system's now-playing controls; Dock menu controls on macOS and taskbar buttons on Windows.
* Volume keys can control MaojuPlayer's volume (Windows, and Linux under X11).
* **Update notification:** Help → About → "Check for updates automatically" (on by default, at most once a day at startup) and "Check now". MaojuPlayer only reads the latest release information from this repository; nothing is downloaded or installed.

### 🌍 Languages

* The interface is available in 96 languages (English plus 95 translations).
* Arabic, Hebrew, Persian and Urdu are marked *experimental*: right-to-left text is not laid out yet.
* Built-in fonts cover many writing systems (including Chinese, Korean, Arabic, Hebrew, Devanagari and Bengali), so no extra font install is needed.

### 💻 Platform notes

* **macOS:** Apple Silicon (ARM64), CoreAudio output.
* **Windows:** 10 / 11, x64, WASAPI (shared and exclusive) and ASIO output.
* **Linux:** x64, ALSA output (PipeWire and PulseAudio through their ALSA devices).
* **Linux ARM64:** experimental build.
* The computer is kept from going to sleep while music plays; the display can still sleep.
* Every release includes a `SHA256SUMS` file to check your download.

### ⚠️ Known limitations

* **Windows:** install Microsoft's Visual C++ Redistributable (x64) first, or MaojuPlayer does not start ("VCRUNTIME140.dll was not found"). Get it from [vc_redist.x64.exe](https://aka.ms/vc14/vc_redist.x64.exe) or run `winget install Microsoft.VCRedist.2015+.x64`.
* **Linux ARM64:** experimental (cross-compiled, not tested), and WavPack files are not supported in this build.
* **Right-to-left languages** (Arabic, Hebrew, Persian, Urdu) are experimental: text may be left-aligned, and mixed right-to-left and Latin text may appear in the wrong order.
* **Builds are not code-signed:** macOS Gatekeeper and Windows SmartScreen show a warning on first launch. See *First launch* in the [README](README.md).
* **DSD512 and higher:** DoP stops at DSD256, and native DSD is only available through ASIO (Windows) or an exclusive ALSA device (Linux). On macOS, DSD512 is always converted to PCM.
* DoP and native DSD bypass all DSP: software volume, balance, EQ and crossfeed do not apply. Use your DAC's volume.
* **Tidal:** there is no Featured tab.
* Volume keys cannot be taken over on macOS or in a Wayland session.
* **Roon:** MaojuPlayer is a controller only, not a Roon audio endpoint; audio plays on the Roon zone.
