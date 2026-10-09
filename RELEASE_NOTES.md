# KŌRA 0.2.43 — public beta

This beta provides separate **Apple Silicon**, **Intel Mac** and **Windows x64**
packages. It also adds experimental Kodachrome 64 alongside the Fujifilm looks.

Get the [0.2.43 release](https://github.com/avogadro-bit/kora/releases/tag/v0.2.43)
or the [matching source code](https://github.com/avogadro-bit/kora-source/tree/v0.2.43).
Quit the old version before replacing it. Installed LUTs and preferences retain
their existing locations. Fujifilm LUTs remain a separate installation through
Setup; Kodachrome data is included.

## Performance and portability

- Reuse the reduced RAW buffer across adjustments. In six local trials on a
  60.5 MP DNG, median 1800-pixel Kodachrome preview calculation fell from **276 ms
  to 124 ms**, with identical decoded JPEG pixels. This is a warm-preview result:
  the RAW was already loaded, and the first RAW decode is not accelerated.
- Bound concurrent batch exports and release JPEG results once written to the ZIP.
  A 32-image, two-worker test retained at most two JPEG results instead of 32;
  this is not a measurement of total RAW-processing memory.
- Cache repeated metadata reads, invalidate them when the file or selected tool
  changes, and pass Windows photo paths to ExifTool as UTF-8.
- Detect optional Windows ExifTool beside the app or under the user's Kora tools
  directory, without requiring a PATH change. ExifTool is not bundled.
- Build and audit each architecture separately, including model integrity,
  essential resources, native library architecture and macOS deployment targets.
- Compile the Intel RAW engine from verified sources with the same RAW codec
  features enabled as the Apple Silicon build.

## Requirements and actual checks

Both Mac packages require **macOS 14 or later**. The Windows x64 target is
**Windows 10 22H2 or Windows 11**, with **WebView2 Evergreen Runtime and .NET
Framework 4.8**. Windows 11 ARM runs this package through x64 emulation. Python
is bundled on all platforms. macOS 12/13 and Windows 10 ARM are not targets.

- **Mac:** Apple Silicon native and Intel under Rosetta, on macOS 27 / M4 Max.
  After relocation to Unicode paths, both packaged local services produced a
  Kodachrome preview, detail tile and full-resolution 60.5 MP JPEG with an ICC
  profile, without Fujifilm LUTs. Original RAW checksums remained unchanged.
  This did not test the native Mac window. Audits passed for 139 ARM and 156 Intel
  native components, with a maximum declared macOS requirement of 14.0.
- **Windows:** x64 package in Windows 11 ARM64 (build 26300), using x64 emulation.
  The relocated application passed its actual WebView2 window check, Unicode
  paths, Provia/Classic Negative/Pro Neg Hi/Kodachrome previews, detail and JPEG
  export with an ICC profile. Its audit passed for 126 native components.
- **Automated checks:** the Mac suite passed 311 Python and 17 JavaScript tests;
  nine portability tests passed after the final fixes. The Windows suite ran
  311 tests: 285 passed and 26 skipped because Fuji assets were absent. A later
  packaged test used verified official LUTs temporarily to exercise those films.

Windows 10, an actual macOS 14 installation, a physical Intel Mac and a physical
Intel/AMD Windows PC remain untested. CI workflows are configured but no CI pass
is claimed for this release. The [portability report](https://github.com/avogadro-bit/kora-source/blob/v0.2.43/docs/PORTABILITY.md)
documents the test scope and remaining checks.

This remains an evaluation beta. The Mac apps are ad-hoc signed and not
Apple-notarized; the Windows app has no publisher signature. Kodachrome is an
experimental reconstruction, not a validated match to physical film, and the
Fuji adaptation is not a camera-calibrated reproduction of camera JPEG output.

Platform-specific notice and dependency-source ZIPs accompany the applications.
See [third-party information](THIRD_PARTY.md) and `SHA256SUMS.txt` in the release.

## Previous release: KŌRA 0.2.21 — public beta

Film Recipe Lab is now KŌRA. For Apple Silicon Macs running macOS 14 or later.

- Quiet graphite interface, updated icon, full-screen launch and more image space.
- RAW and JPEG export optimizations, including grain processing.
- Highlight rendering fixes and improved source-detail handling.
- Persistent error logging and a folder-based JSON recipe menu.
- Directional colors in white balance controls.
- Only ten official-LUT simulations are selectable; legacy recipes retain their rendering.
- Removed the unavailable Lens Modulation Optimizer and Multi-exposure HDR controls.

Download **Kora-0.2.21-macOS-arm64.dmg** from the
[release page](https://github.com/avogadro-bit/kora/releases/tag/v0.2.21).
Quit the old app first, install KŌRA in Applications, and launch KŌRA.
Installed LUTs and preferences retain their existing storage locations.

192 Python tests pass, along with JavaScript syntax and film-menu checks.
The DMG and release-file checksums were verified locally.
This remains an evaluation beta, not Apple-notarized or a camera-calibrated Fuji engine.

## Previous release: Film Recipe Lab 0.2.7 — public beta

For Apple Silicon Macs running macOS 14 or later.

Changes since public beta 0.2.3:

- Proper macOS reopen handling from Finder or the Dock, and clean shutdown on Quit.
- Expandable folder tree, selected-folder path, and optional subfolder inclusion.
- All photos accessible in the carousel, with thumbnails loaded as they become visible.
- Detection of standard Homebrew and MacPorts ExifTool installations without a
  Terminal PATH. ExifTool remains optional and is not bundled.
- Leica DNG distortion correction calculated for requested detail regions instead
  of correcting the entire full-resolution frame before showing a tile.
- Superseded viewport requests rejected before further expensive work; detail
  tiles nearest the viewport center are prioritized.
- Connection warnings tolerate isolated delays and distinguish slow responses
  from expired sessions. Checking the connection no longer reloads the editor.
- Smaller top and bottom bars leave more room for the image; panels remain resizable.

Download **Film-Recipe-Lab-0.2.7-macOS-arm64.dmg** to install the app. The ZIP is
an alternative packaging of the same application. The two dependency archives
are provided for license/source information and are not required to run the app.

Official LUTs are installed separately through Setup. Existing users should quit
the previous application before replacing it; installed LUTs are preserved.

This is an evaluation beta, not an exact reproduction of Fujifilm camera output.
Camera support and processing performance vary. Not Apple-notarized.

The first full-resolution zoom still requires RAW decoding and can take several
seconds on large files. Subsequent regions use the decoded buffer and tile cache.
Regional Leica correction was checked against full-frame output. 164 Python tests
and the JavaScript connection-state checks pass locally. See the README for details.
