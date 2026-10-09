# KŌRA — public beta

A local RAW photo editor for exploring film-inspired looks, with individual and
group adjustments, source-resolution detail, and JPEG/TIFF export.
A quiet, photograph-first workspace. Formerly Film Recipe Lab.

This project is developed with the help of AI coding tools.

**[Download KŌRA 0.2.43 — public beta](https://github.com/avogadro-bit/kora/releases/tag/v0.2.43)**

| Computer | Download | Requirements |
| --- | --- | --- |
| Mac Apple Silicon (M1 or newer) | [ARM64 DMG](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-macOS-arm64.dmg) | macOS 14 or later |
| Mac Intel | [Intel DMG](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-macOS-x86_64.dmg) | macOS 14 or later |
| Windows Intel/AMD, or Windows 11 ARM | [Windows x64 ZIP](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-Windows-x64.zip) | Target: Windows 10 22H2 / Windows 11; WebView2 and .NET Framework 4.8 |

Python is included. Windows 11 ARM uses x64 emulation, not a native ARM build.
These are compatibility targets; see the actual tests and remaining checks below.
The Mac apps are ad-hoc signed, not Apple-notarized. The Windows app has no
publisher signature. ZIP alternatives for both Mac builds are on the release page.

## Start editing

1. Quit the previous version. On Mac, open the matching DMG, copy **KŌRA** to
   Applications and launch it. On Windows, extract the entire ZIP and launch
   `Kora/Kora.exe`; keep `_internal` beside the executable. The editor opens in
   its own window and runs locally on your computer.
2. On Windows, install the [Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/)
   and .NET Framework 4.8 if they are missing. Do not run Kora from inside the ZIP.
3. For the Fujifilm looks, in **Setup**, follow **Download from Fujifilm** to obtain the official
   **GFX ETERNA 55 v1.10** LUT pack and review Fujifilm's terms.
4. Use **Choose Downloaded ZIP** or **Choose Extracted Folder**. The application
   checks all ten LUTs before installing them. Other camera packs are not accepted.
5. Choose **Open Folder**, select your RAW photographs and start editing.

The Fujifilm LUTs are a separate download; they are not included with the app.
Experimental **Kodachrome 64** is included as a special film and works without them.
On macOS, installed LUTs are kept in `~/.local/share/fuji-recipe-lab/luts` across app updates.
On Windows, they are kept in `%LOCALAPPDATA%\Kora\luts`.
The application processes your images locally and does not upload your photos
to a cloud service. Downloads from GitHub/Fujifilm require an internet connection.
Original photo files are read in place; exports are separate files.

## What you can try

- RAW formats supported by the bundled LibRaw decoder, including RAF, DNG, CR3,
  NEF, ARW, RW2 and ORF; support depends on the camera model and compression.
- Ten official LUT-based looks, including PROVIA, Velvia, ASTIA, Classic Chrome,
  Classic Neg., REALA ACE and ACROS, through an independent photo adaptation.
- Experimental Kodachrome 64, using the included spectral reconstruction model.
- Exposure, highlights, whites, shadows, blacks, white balance, color and grain.
- Multi-photo selection, shared adjustments and batch JPEG export.
- Zoomable preview and source-resolution detail; lens corrections where supported.
- Expandable folder tree and compact, resizable viewer panels.
- A folder-based recipe library and seven local recipe slots.
- Colored white balance axes and persistent error logs for troubleshooting.

## Changes and validation in 0.2.43

Repeated adjustments reuse a reduced RAW buffer. On a 60.5 MP DNG, a warm
1800-pixel Kodachrome preview took **124 ms instead of 276 ms** in the local
benchmark (six trials, identical decoded JPEG pixels). This measures preview
calculation after loading; it does not accelerate the first RAW decode or measure
the complete interface response. Batch export also releases each JPEG after writing
it to the ZIP, and repeated metadata reads use a bounded cache. Windows metadata
paths support accents and non-Latin characters.

The packaged Apple Silicon app and Intel app under Rosetta passed preview, detail
and full-resolution JPEG export tests on **macOS 27 / M4 Max**, after relocation
to a path containing spaces and accents. These tests exercised the packaged local
service, not the native Mac window. The Windows x64 app passed an actual WebView2
window check and RAW preview/detail/export tests in **Windows 11 ARM64**, using
x64 emulation. Binary and resource audits passed for all three packages.

**Not yet verified:** macOS 14 on a real installation, other older Mac versions,
a physical Intel Mac, Windows 10, or a physical Intel/AMD Windows PC. Configured
CI workflows are not evidence that those platforms have passed. See the
[release notes](RELEASE_NOTES.md) and [detailed validation](https://github.com/avogadro-bit/kora-source/blob/v0.2.43/docs/PORTABILITY.md).

## Beta limitations

This is an independent project, not a Fujifilm product or a reproduction of the
camera's JPEG engine. The official LUTs were designed for video; their adaptation
to photographic RAW files is not camera-calibrated. Results will vary by camera.
The white-balance controls include documented X-T4-derived coefficients and do not
claim X100VI calibration. Large RAW files can still take time to process.
Kodachrome 64 is an experimental reconstruction, not a verified reproduction of
physical film across cameras, scenes and exposure conditions. It is not affiliated
with or endorsed by Kodak.

ExifTool is optional and is not bundled. Without it, some shooting metadata and
lens profiles are unavailable; basic DNG camera identification works without it.
Standard Homebrew and MacPorts ExifTool installations are detected even when
the app is launched from Finder or the Dock.
On Windows, ExifTool can be installed at `tools\exiftool.exe` beside `Kora.exe`
or at `%LOCALAPPDATA%\Kora\tools\exiftool.exe`. Keep its companion
`exiftool_files` folder beside it; these locations need no PATH change.
Adobe RGB export depends on an available system profile; sRGB is the
portable choice. Please treat this as software for evaluation and report issues.

## Feedback

[Report a bug or suggestion](https://github.com/avogadro-bit/kora/issues/new/choose).
Include the app version, operating system version, computer model, camera/RAW format, steps to
reproduce, and expected versus actual behavior. Attach screenshots or sample
photos only if you want them publicly visible and have permission to share them.
Never post private photographs or a local session URL containing `#session=`.

## Licenses and source components

This repository hosts public downloads and documentation; the
[0.2.43 source code](https://github.com/avogadro-bit/kora-source/tree/v0.2.43)
is in the development repository and supplied as a release archive.
Original KŌRA code is MIT-licensed; third-party
components retain their respective licenses.

The release includes separate **Third-Party-Notices** and **Dependency-Sources**
ZIPs for `macOS-arm64`, `macOS-x86_64` and `Windows-x64`; choose the same platform
as your app. Notices are also inside the Mac app at
`Contents/Resources/Third-Party-Notices`, and beside `Kora.exe` under
`_internal/Third-Party-Notices` on Windows.
See [third-party notices](THIRD_PARTY.md) for attribution, source availability and
library replacement information. Official LUTs and firmware are not redistributed.
`SHA256SUMS.txt` lists checksums for the supplied release files.
