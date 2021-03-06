---
description: >-
  mpg123 is a free and open-source audio player. It supports MPEG audio formats,
  including MP3.
---

# mpg123

## How do I convert an MP3 file to WAV format under Linux using a shell prompt?

There are plenty of tools that to convert an MP3 file into WAV format. I recommend mpg321 which is a free command-line mp3 player, which uses the mad audio decoding library. Install mpg321 or mpg123 Type the following command under Debian / Ubuntu Linux, enter:

```text
sudo apt-get install mpg321
```

OR

```text
sudo apt-get install mpg123
```

I recommend using mpg123 as it is updated frequently. Install mpg123 under CentOS / RHEL / Fedora Linux. Turn on rpmforge repo and type the following command:

```text
yum install mpg123
```

## Convert an MP3 to WAV

The -w option will convert an .mp3 file to .wav file. The syntax is:

```text
mpg123 -w output.wav input.mp3
```

OR

```text
mpg321 -w output.wav input.mp3
```

## A Sample Shell Script Helper Function

Add the following to your ~/.bashrc startup file \(tested with bash v3.x+\):

```bash
mp3towav(){
    [[ $# -eq 0 ]] && { echo "mp3wav mp3file"; exit 1; }
    for i in "$@"
    do
        # create .wav file name
        local out="${i%/*}.wav"
        [[ -f "$i" ]] && { echo -n "Processing ${i}..."; mpg123 -w "${out}" "$i" &>/dev/null  && echo "done." || echo "failed."; }
    done
}
```

Use it as follows:

```bash
mp3towav *.mp3
mp3towav "this is a test.mp3"
ls *.wav
```

