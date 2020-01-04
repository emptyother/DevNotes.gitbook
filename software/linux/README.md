---
description: Tips and tricks for the best Operating System that I never use.
---

# Linux

## Linux terminology

| Word | Definition |
| :--- | :--- |
| Desktop Environment | Taskbar, start menu. Can run different _Window Managers_, or comes with its own. |
| Window Manager | Handles moving windows around \(or not, might be a tiling window manager or such\). |
| Display Managers | The login screen, handles starting up the _Desktop Environment_. |
| Shell | Command line backend. The one that runs your script. |
| Terminal | Command line frontend. The window you write text in and read output from. It handles text input and keyboard shortcuts. |

## Terminal commands

| Command | Description |
| :--- | :--- |
| apt | package mangager for Ubuntu, alias for apt-get. |
| sudo -s | Permanent sudo, no need to write "sudo" after each. |
| ls -lh | List files with human-readable details. |
| cp -rp \[source\]\[target\] | Copy all files including permissions \(-r recursive, -p preserve permissions\). |
| gunzip file.gz | Unzip gzip files. |
| gzip -d file.gz | Unzip gzip files. |
| chmod | Setting permissions. |
| chown | Setting ownership. Can also set group. |
| chgrp | Setting group ownership. |

## Useful paths in linux

| Path | Description |
| :--- | :--- |
| /etc/apt/sources.list.d | List of feeds for apt-get, the package manager. |
| /etc/apt/trusted.gpg.d | Security sertificates for connecting to apt-get feeds. |

