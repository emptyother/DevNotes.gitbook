# Google Chrome

## Remote Device debugging

1. Download Android SDK here ("SDK Tools Only" section) and unzip the content.
2. Run SDK Manager.exe and install Android SDK platform tools
3. Open up the Command prompt (simply by pressing the windows button and type in
   cmd.exe)
4. Enter the path with ex: cd c:/downloads/sdk/platform-tools
5. Open ADB by typing in adb.exe
6. Run the following command by typing it and pressing enter: adb devices
7. Check if you get the prompt on your device, if you still can't see your phone
   in Inspect Devices run the following commands one by one (excluding the ")
   "adb kill-server" "adb start-server" "adb devices"

[Source](http://stackoverflow.com/questions/23648230/chromes-remote-debugging-usb-debugging-not-working-for-samsung-galaxy-s3-runn).

Du kan også installere Android SDK sammen med Visual Studio. I så tilfelle er
path "C:\Program Files (x86)\Android\android-sdk\platform-tools". Punkt 6
starter en debugging service på din lokale maskin.

## Useful command line arguments for Chrome

    --remote-debugging-port=9222

Port 9222 is the port most chrome debugger clients expects.

    --no-first-run
    --no-default-browser-check
    --user-data-dir=<custom data dir>
