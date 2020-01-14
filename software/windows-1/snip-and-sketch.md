---
description: Tweaks for Windows' new snipping program
---

# Snip & Sketch

## Keyboard shortcuts

Various ways of taking screenshots in windows.

| Keys | Command |
| :--- | :--- |
| `Win+Shift+S` | Launch Snip & Sketch in Snip-mode. |
| `PrtScn` | Launch Snip & Sketch in Snip-mode. Only if enabled in Windows Settings. Otherwise it works like `Ctrl+PrtScn`. |
| `Win+PrtScn` | Screenshot all screens and save to file in `Pictures\Screenshots`. _See further down for changing output folder._ |
| `Alt+PrtScn` | Screenshot current Window to clipboard. |
| `Ctrl+PrtScn` | Screenshot all screens. |
| `Win+Alt+PrtScn` | Screenshot current window using Windows' Game Bar and save to a file in `Videos\Recordings`. |

## Changing default screenshot output folder

**The default screenshot location** is a folder called `Screenshots` in your picture folder. If you want to change that, Windows screenshot program itself doesn't have much options but the last comment [here](https://www.tenforums.com/general-support/131419-screenshots-not-being-saved-usual-folder-anymore-2.html) worked for me. Open regedit. Go to the path `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders`. Add a new **expandable string** named `{B7BEDE81-DF94-4682-A7D8-57A52620B86F}`. Open it and enter the path of the folder you want your screenshots to go to. `C:\Users\Username\My Screenshots` for example. Make sure that folder exists. Then restart your computer \(or just explorer.exe\). Next time you use Win+PrtScn now it should go to that folder.

