# Compressarr Presets

The official catalog of extra encoding profiles for [Compressarr](https://github.com/MrWizardCT/Compressarr) 2.2 and later.
Compressarr reads this repository (from its **Profiles > Import > From Catalog** tab) so new profiles can be added without a new
Compressarr release.

The built-in profiles (`Compressarr SD-HD`, `Compressarr UHD AV1`, `HEVC NVENC (fast)`) ship inside Compressarr and are **not**
listed here.

## How it works

- **Nothing is installed automatically.** You open the catalog in Compressarr, tick the profiles you want and import them.
- **Published versions never change.** Every profile has an integer version, and the name you get is `<family> v<N>`, for example
  `Compressarr UHD HEVC (HDR) v1`. Lanes refer to a profile by name, so a profile you already use can never change under you.
  A change - even a one-character fix - is published as a new version, `v2`, which you can add next to `v1`.
- **Everything is checked.** Each file's SHA-256 is listed in `catalog.json`; Compressarr verifies it and runs the profile through
  its own validators before saving it.

## Layout

```
catalog.json                the index: one entry per profile version
profiles/handbrake/*.json   HandBrake preset files (the format HandBrake exports)
profiles/ffmpeg/*.json      Compressarr ffmpeg profiles
CHANGELOG.md                one line per published version
```

### catalog.json

`schema` is the catalog format (currently 1). `catalog` names the source. Each profile entry has:

| Field | Meaning |
|---|---|
| `family`, `version` | the name without the version, and the integer version |
| `engine` | `handbrake` or `ffmpeg` |
| `file`, `sha256` | the profile file and its SHA-256 |
| `minAppVersion` | the oldest Compressarr that can read it |
| `description`, `changelog` | what it is, and what this version changed |
| `published`, `author`, `sourceUrl` | when, who made it, and where it came from (optional credit link) |
| `deprecated` | `null`, or a reason a version should no longer be used (a warning only - installed copies are never changed) |
| `requires` | encoders it needs (`x265`, `av1_nvenc`...) |

## Rules for changing this repository

1. Never edit a published profile file. Add a new version (`v2`) with a new file and a new `catalog.json` entry.
2. Update the SHA-256 in `catalog.json` from the exact bytes of the file.
3. Add a line to `CHANGELOG.md`.
4. A version found to be harmful gets `deprecated` set to a reason; it is never removed.

## The profiles in this catalog

| Profile | Engine | For |
|---|---|---|
| Compressarr UHD HEVC (HDR) | HandBrake | 4K HDR and Dolby Vision movies; keeps HDR10, HDR10+ and Dolby Vision |
| Compressarr HD Quality | HandBrake | 1080p and below, higher quality than SD-HD |
| Compressarr Compatibility (H.264) | HandBrake | SDR content for old players that cannot play H.265 |
| Compressarr AV1 (NVENC) | ffmpeg | RTX 40-series (or newer) GPUs: AV1 at GPU speed |
| Compressarr SD-HD Opus 7.1 | HandBrake and ffmpeg | Like SD-HD, but Opus audio so 7.1 surround is kept (E-AC3 stops at 5.1). Not every TV or box plays Opus |

## Licence

The profiles are settings files, released under the GPLv3 like Compressarr itself. The older
[Handbrake-Custom-Presets](https://github.com/MrWizardCT/Handbrake-Custom-Presets) repository is superseded by this one.
