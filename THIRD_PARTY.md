# Third-party components in KŌRA 0.2.43

KŌRA is independent of Fujifilm and Kodak. Official Fujifilm LUTs, camera firmware,
photographs and proprietary ICC profiles are not distributed with this app.
The LUT installer downloads nothing automatically: users obtain the official
archive from Fujifilm and install their own copy.

Each application bundles Python and third-party libraries. Their original
copyright and license texts and a version inventory are in its matching
Third-Party-Notices archive, and in the installed application:

- Mac: `KŌRA.app/Contents/Resources/Third-Party-Notices`.
- Windows: `_internal/Third-Party-Notices` beside `Kora.exe`.

These licenses continue to govern their respective components.
No additional restriction on modifying, replacing or reverse engineering these
components for debugging such modifications is imposed by KŌRA.

## Components and attribution

- Python: Python Software Foundation license and included third-party notices.
- PyObjC core and Cocoa bindings: MIT license, Ronald Oussoren and contributors.
- Windows uses pywebview, Python.NET and clr_loader under their included license
  texts. The bundled WebView2 bridge/loader retains Microsoft's terms; the
  WebView2 browser runtime and .NET Framework 4.8 are installed separately.
- rawpy: MIT, Copyright Maik Riechert. LibRaw: LGPL 2.1, Copyright LibRaw LLC
  and contributors; its additional attributions are preserved in the source archive.
- lensfunpy: MIT, Copyright Maik Riechert. Lensfun library: LGPL 3.0.
  Lensfun's unmodified camera/lens database: CC BY-SA 3.0, Lensfun contributors,
  https://lensfun.github.io/ and https://github.com/lensfun/lensfun.
- GLib: LGPL 2.1 or later; gettext libintl: LGPL 2.1 or later.
  PCRE2 and libffi retain their upstream licenses and copyright notices.
- NumPy and SciPy: BSD licenses with the bundled upstream notices for numerical
  libraries, including OpenBLAS and compiler runtimes where applicable.
- Pillow and its codec libraries: see the comprehensive Pillow license text.
  This software is based in part on the work of the Independent JPEG Group
  and the FreeType Team (https://www.freetype.org/).
- Pydantic, pydantic-core, annotated-types, typing-inspection and tifffile:
  their included MIT license texts. typing_extensions: PSF license.
  packaging: Apache 2.0 / BSD, as described in its license files.
- OpenSSL, zstd, mpdecimal, libjpeg-turbo, JasPer and Little CMS:
  see the included component notices.

## Corresponding sources and replacement

The [0.2.43 release](https://github.com/avogadro-bit/kora/releases/tag/v0.2.43)
provides matching archives for each platform. Use the pair corresponding to the
application you downloaded; their dependency inventories differ.

| Platform | Notices | Dependency sources |
| --- | --- | --- |
| Mac Apple Silicon | [Third-Party-Notices](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-macOS-arm64-Third-Party-Notices.zip) | [Dependency-Sources](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-macOS-arm64-Dependency-Sources.zip) |
| Mac Intel | [Third-Party-Notices](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-macOS-x86_64-Third-Party-Notices.zip) | [Dependency-Sources](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-macOS-x86_64-Dependency-Sources.zip) |
| Windows x64 | [Third-Party-Notices](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-Windows-x64-Third-Party-Notices.zip) | [Dependency-Sources](https://github.com/avogadro-bit/kora/releases/download/v0.2.43/Kora-0.2.43-Windows-x64-Dependency-Sources.zip) |

Dependency archives contain the matching upstream sources for components such
as LibRaw, rawpy, Lensfun, lensfunpy, GLib, gettext, PCRE2, libffi,
libjpeg-turbo, JasPer and Little CMS, as applicable to that build.
`inventory.json` records revisions, original URLs and SHA-256 checksums.
The rawpy and lensfunpy archives include their build scripts under `.github/scripts`.
Place the separately supplied LibRaw / LibRaw-cmake and Lensfun sources in the
corresponding `external/` directories when rebuilding these wrappers.

These components are used without application-specific source modifications.
Mac packaging changes their library load paths and adds an ad-hoc signature.
Native libraries are separate files in the Mac app's `Contents/Frameworks`
directory, or the Windows app's `_internal` directory (including rawpy and
lensfunpy subdirectories); Python extensions can likewise
be replaced with ABI-compatible builds for the Python version in the inventory.
On Mac, replacing a signed file requires locally re-signing the modified app, for example
`codesign --force --deep --sign - "KŌRA.app"`.
The application contains no license check preventing such replacement.

The [original KŌRA code](https://github.com/avogadro-bit/kora-source/tree/v0.2.43)
is MIT-licensed and includes build scripts and the experimental Kodachrome
model's provenance. That license does not replace
the licenses of the components above or grant rights to Fujifilm assets.
