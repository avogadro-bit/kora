# KŌRA — public beta

A local RAW photo editor for exploring film-inspired looks, with individual and
group adjustments, source-resolution detail, and JPEG/TIFF export.
A quiet, photograph-first workspace. Formerly Film Recipe Lab.

This project is developed with the help of AI coding tools.

**[Download KŌRA 0.2.21 for macOS](https://github.com/avogadro-bit/kora/releases/tag/v0.2.21)**

**[Download KŌRA 0.2.21 for Windows x64](https://github.com/avogadro-bit/kora/releases/download/v0.2.21/Kora-0.2.21-Windows-x64.zip)**

**macOS:** Apple Silicon Mac (M1 or newer), macOS 14 or later. Not Apple-notarized.
**Windows:** Windows 10/11 x64 (Intel/AMD), .NET Framework 4.8 and
[Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/).
The Windows build is unsigned. Python is included on both platforms.
No native Windows ARM64 or Intel Mac build is available.

## Windows installation

Download `Kora-0.2.21-Windows-x64.zip`, extract the **entire** ZIP, then launch
`Kora.exe`. Keep the `_internal` folder beside the executable. Do not run it from
inside the ZIP. Install the official LUTs through Setup as described below.
The app opens full screen; its fullscreen button returns to a normal window.

Windows data is stored in `%LOCALAPPDATA%\Kora`: `luts` for LUTs, `WebView` for
preferences and `Logs\errors.jsonl` for diagnostics. Make cloud photos available
offline before opening them. Adobe RGB export needs an installed Adobe RGB ICC
profile; sRGB needs no extra profile.

This first Windows beta was compiled on Windows and passed automated server and
WebView2 window checks. Its 200-test suite passed with 21 skips (including tests
requiring external LUTs). Real-photo workflow testing on user PCs is still needed.

## Start editing on macOS

1. Download `Kora-0.2.21-macOS-arm64.dmg` from the release assets.
2. Copy **KŌRA** to Applications and launch it. The editor opens in its own
   macOS window, in full screen by default, and runs locally on your computer.
   Quit the old Film Recipe Lab app before installing; launch KŌRA afterward.
3. In **Setup**, follow **Download from Fujifilm** to obtain the official
   **GFX ETERNA 55 v1.10** LUT pack and review Fujifilm's terms.
4. Use **Choose Downloaded ZIP** or **Choose Extracted Folder**. The application
   checks all ten LUTs before installing them. Other camera packs are not accepted.
5. Choose **Open Folder**, select your RAW photographs and start editing.

The film LUTs are a separate download; they are not included with the app.
On macOS, installed LUTs are kept in `~/.local/share/fuji-recipe-lab/luts` across app updates.
The application processes your images locally and does not upload your photos
to a cloud service. Downloads from GitHub/Fujifilm require an internet connection.
Original photo files are read in place; exports are separate files.

## What you can try

- RAW formats supported by the bundled LibRaw decoder, including RAF, DNG, CR3,
  NEF, ARW, RW2 and ORF; support depends on the camera model and compression.
- Ten official LUT-based looks, including PROVIA, Velvia, ASTIA, Classic Chrome,
  Classic Neg., REALA ACE and ACROS, through an independent photo adaptation.
- Exposure, highlights, whites, shadows, blacks, white balance, color and grain.
- Multi-photo selection, shared adjustments and batch JPEG export.
- Zoomable preview and source-resolution detail; lens corrections where supported.
- Expandable folder tree and compact, resizable viewer panels.
- A folder-based recipe library and seven local recipe slots.
- Colored white balance axes and persistent error logs for troubleshooting.

## Beta limitations

This is an independent project, not a Fujifilm product or a reproduction of the
camera's JPEG engine. The official LUTs were designed for video; their adaptation
to photographic RAW files is not camera-calibrated. Results will vary by camera.
The white-balance controls include documented X-T4-derived coefficients and do not
claim X100VI calibration. Large RAW files can still take time to process.

ExifTool is optional and is not bundled. Without it, some shooting metadata and
lens profiles are unavailable; basic DNG camera identification works without it.
Standard Homebrew and MacPorts ExifTool installations are detected even when
the app is launched from Finder or the Dock.
Adobe RGB export depends on an available macOS system profile; sRGB is the
portable choice. Please treat this as software for evaluation and report issues.

## Feedback

[Report a bug or suggestion](https://github.com/avogadro-bit/kora/issues/new/choose).
Include the app version, operating system version, computer model, camera/RAW format, steps to
reproduce, and expected versus actual behavior. Attach screenshots or sample
photos only if you want them publicly visible and have permission to share them.
Never post private photographs or a local session URL containing `#session=`.

## Licenses and source components

This repository hosts public downloads and documentation; the development
repository is separate. Original KŌRA code is MIT-licensed; third-party
components retain their respective licenses.

The release includes **Third-Party-Notices.zip** and **Dependency-Sources.zip**.
Windows has separate archives with the `-Windows` suffix and
`SHA256SUMS-Windows.txt`; use the notices and sources matching your platform.
Notices are also inside the app at `Contents/Resources/Third-Party-Notices`.
See [third-party notices](THIRD_PARTY.md) for attribution, source availability and
library replacement information. Official LUTs and firmware are not redistributed.
`SHA256SUMS.txt` lists checksums for the four downloadable archives/installers.
