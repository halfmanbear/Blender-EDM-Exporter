# Official development release sync

Imported from the supplied `io_scene_edm-270115` directory on 2026-11-19.
The release folder is labelled 270115, but its `bl_info` version is
`(1, 0, "269672")`; the fork uses that supplied version unchanged.

Updated both bundled native exporters (`pyedm_311.pyd` and `pyedm_313.pyd`)
with byte-identical copies from the release. All other release assets and
Python files already matched the fork apart from version metadata and the
custom fixes listed below. The supplied changelog contains no additional
entries documenting the native changes.

Preserved fork fixes:

- Load modules and assets relative to the installed plugin, including symlinks.
- Convert light socket RGBA values to RGB for native `PropertyFloat3`.
- Restore CombineRGB nodes correctly and retain serializer node-type fallback.
- Retain the corrected glass normal socket name and existing opacity Fresnel
  support; these already match the supplied release.

Validation: all plugin Python files parse; both native binaries match the
release by SHA-256. The Python 3.11 native module imports successfully.
In an isolated Blender 5.3 background process, the Python 3.13 native module
loads, the addon registers/unregisters, and CombineRGB reconstruction, RGB
conversion, and plugin asset paths pass smoke checks. Full scene export and
visual comparison in DCS have not been tested.
