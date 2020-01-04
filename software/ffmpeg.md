# FFMPEG

## Convert Video With FFMPEG

### Add logo

```text
.\ffmpeg.exe -i 11085.2b.mp4 -i logo.png -filter_complex "overlay=W-w-20:20" -codec:a copy wlogo.mp4
```

### Convert and scale

Make sure bitrate isn't higher than the original file \(downadjust the 3200000 value to whatever the original was\).

```text
.\ffmpeg.exe -i wlogo.mp4 -c:v libx264 -b:v 1600000 -vf scale=1280:-1 .\HD\11085.2b.mp4 -movflags faststart
.\ffmpeg.exe -i wlogo.mp4 -c:v libx264 -b:v 600000 -vf scale=480:-1 .\480p\11085.2b.mp4 -movflags faststart
```

