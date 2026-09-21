# Third-party components in the macOS application

KŌRA is independent of Fujifilm. Official LUTs, camera firmware,
photographs and proprietary ICC profiles are not distributed with this app.
The LUT installer downloads nothing automatically: users obtain the official
archive from Fujifilm and install their own copy.

The executable bundles Python and third-party libraries. Their original
copyright and license texts are supplied in this directory, together with a
version inventory. These licenses continue to govern their respective components.
No additional restriction on modifying, replacing or reverse engineering these
components for debugging such modifications is imposed by KŌRA.

## Components and attribution

- Python: Python Software Foundation license and included third-party notices.
- PyObjC core and Cocoa bindings: MIT license, Ronald Oussoren and contributors.
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

The public beta release provides `Dependency-Sources.zip` at
https://github.com/avogadro-bit/kora/releases.
It contains the matching upstream LibRaw, rawpy, Lensfun, lensfunpy, GLib,
gettext, PCRE2, libffi, libjpeg-turbo, JasPer and Little CMS source archives.
`inventory.json` records revisions, original URLs and SHA-256 checksums.
The rawpy and lensfunpy archives include their build scripts under `.github/scripts`.
Place the separately supplied LibRaw / LibRaw-cmake and Lensfun sources in the
corresponding `external/` directories when rebuilding these wrappers.

These components are used without application-specific source modifications.
Packaging changes their library load paths and adds the existing ad-hoc signature.
Native libraries are separate files in the app's `Contents/Frameworks` directory
(including rawpy and lensfunpy subdirectories); Python extensions can likewise
be replaced with ABI-compatible builds for the Python version in the inventory.
Replacing a signed file requires locally re-signing the modified app, for example
`codesign --force --deep --sign - "KŌRA.app"`.
The application contains no license check preventing such replacement.

The original KŌRA code is MIT-licensed. That license does not replace
the licenses of the components above or grant rights to Fujifilm assets.
