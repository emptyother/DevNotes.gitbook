---
description: >-
  FFmpeg is a free and open-source project consisting of a vast software suite
  of libraries and programs for handling video, audio, and other multimedia
  files and streams.
---

# FFMPEG

## Convert Video With FFMPEG

### Add logo

```bash
ffmpeg.exe -i inputfile.mp4 -i logo.png -filter_complex "overlay=W-w-20:20" -codec:a copy outputfile.mp4
```

### Convert and scale

Make sure bitrate isn't higher than the original file \(downadjust the 3200000 value to whatever the original was\).

```bash
ffmpeg.exe -i inputfile.mp4 -c:v libx264 -b:v 1600000 -vf scale=1280:-1 .\outputfile.1280p.mp4 -movflags faststart
ffmpeg.exe -i inputfile.mp4 -c:v libx264 -b:v 600000 -vf scale=480:-1 .\outputfile.480p.mp4 -movflags faststart
```

