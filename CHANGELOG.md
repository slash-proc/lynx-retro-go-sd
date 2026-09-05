# Changelog

## [v0.0.2] - 2026-09-06

### Added

- Published under the [GWRG distribution
  spec](https://github.com/slash-proc/gwrg-dist-spec): a `manifest.json`
  describing this core and the systems it provides, an offline bundle, and a
  GitHub Pages mirror of `dist/` that a web installer can read without a human
  in the loop.
- `symbols[]` publishes the linked ELF so a crash address from a device can be
  resolved back to a function. It is named by the manifest and mirrored, but is
  not part of the install set and never reaches the card.
- `gwrg.json`, the hand-written half of the manifest: the short console name,
  whether compressed ROMs work, and any BIOS this core needs. Everything else —
  the systems, their folders, extensions and browse mode, the firmware ABI,
  sizes and hashes — is derived from the packed binary at release time.
- No BIOS is declared, deliberately: Handy synthesises the Lynx boot ROM in
  code, which is worth stating because the opposite is usually assumed.

### Changed

- `scripts/make_manifest.py`, `build_dist.py`, `make_bundle.py` and
  `stage_release.py` are now the shared copies, byte-identical across every
  project. A script that has to be edited on the way in is a script that drifts.


## [v0.0.1]

### Added

- initial release

### Changed

### Fixed

### Install

**Core (`PROJECT_KIND=core`, default)**

- Copy `example.bin` to `/cores/` on the SD card.
- Place test ROMs under `/roms/example/` (dirname matches `CORE_NAME` in the
  Makefile).
- Requires firmware whose ABI matches `SDK_VERSION` in this repository.
