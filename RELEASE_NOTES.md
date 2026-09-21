# KŌRA 0.2.21 — public beta

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
