---
description: >-
  Anything related to our favorite privacy-leaking browser out there.. And its
  children Chromium and Edgium (the new Microsoft Edge).
---

# Google Chrome

## Remote Device debugging

1. Download Android SDK here \("SDK Tools Only" section\) and unzip the content.
2. Run SDK Manager.exe and install Android SDK platform tools
3. Open up the Command prompt.
4. Enter the path with ex: cd c:/downloads/sdk/platform-tools
5. Open ADB by typing in adb.exe
6. Run the following command by typing it and pressing enter: adb devices
7. Check if you get the prompt on your device, if you still can't see your phone

   in Inspect Devices run the following commands one by one

   1. `adb kill-server`
   2. `adb start-server`
   3. `adb devices`

**Source**: [https://stackoverflow.com/questions/23648230/](https://stackoverflow.com/questions/23648230/)

## Useful command line arguments for Chrome

```bash
--remote-debugging-port=9222
```

Port 9222 is the port most chrome debugger clients expects.

```bash
--no-first-run
--no-default-browser-check
--user-data-dir=<custom data dir>
```

## CORS Requests are hidden in Chrome network tab

To show CORS request in Chrome network tab \(it has been disabled for performance reasons\), go to `chrome://flags/#out-of-blink-cors` and disable that setting.

