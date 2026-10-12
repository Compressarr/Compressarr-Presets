# Changelog

One line per published profile version. Published versions never change; a change is a new version.

## 2026-10-11

- **Compressarr UHD HEVC (HDR) v1** (HandBrake): x265 10-bit, RF 22, preset fast; keeps HDR10, HDR10+ and Dolby Vision; every English audio track passed through.
- **Compressarr HD Quality v1** (HandBrake): x265 10-bit, RF 20, preset fast; E-AC3 audio up to 7.1.
- **Compressarr Compatibility (H.264) v1** (HandBrake): x264 8-bit main@4.0, RF 24, veryfast, MP4, 30 fps cap, AAC audio. SDR only.
- **Compressarr AV1 (NVENC) v1** (ffmpeg): av1_nvenc 10-bit, cq 34, preset p5. Needs an RTX 40-series or newer GPU.

- **Compressarr SD-HD Opus 7.1 v1** (HandBrake and ffmpeg): the same as Compressarr SD-HD but the first English audio track is Opus 7.1 at 512 kbps, so 7.1 surround is kept (E-AC3 cannot carry it). Opus is not played by every TV or box.

## 2026-10-12

- Metadata only: the author and maintainer shown for every profile are now **Compressarr**. No profile changed; every profile file and checksum is exactly as published.
