---
description: Anything related to SteelSeries keyboards and mouse and other hardware.
---

# SteelSeries

## SteelSeries SDK

The device _\(a Steelseries Apex M800 Series keyboard\)_ runs a local webservice to listen for JSON webrequests. It then uses that data with one of its own scripts written in GoLisp, a programming language created by Steelseries.

|  | Links |
| :--- | :--- |
| Sourcecode | [https://github.com/SteelSeries/gamesense-sdk/](https://github.com/SteelSeries/gamesense-sdk/) |
| Tutorial | [https://github.com/SteelSeries/gamesense-sdk/blob/master/doc/tutorials/audiovisualizer\_tutorial.md](https://github.com/SteelSeries/gamesense-sdk/blob/master/doc/tutorials/audiovisualizer_tutorial.md) |

|  | Paths |
| :--- | :--- |
| Server url and port: | `C:\ProgramData\SteelSeries\SteelSeries Engine 3\coreProps.json` |
| Device Script folder: | `C:\ProgramData\SteelSeries\SteelSeries Engine 3\hax0rBindings\` |

### Example Script 1 \(client/game\)

This sends a webrequest to the already existing "Audiovisualizer.lsp" device script.

```text
$url = "http://127.0.0.1:58956/game_event";
$json2 = @"
{"game":"AUDIOVISUALIZER","event":"AUDIO","data":{"values":[0,20,40,60,80,100,120,140,160,180,200,220,240,260,140,141,136,143,140,137,141,148,147]}}
"@; Invoke-WebRequest -Method POST -Uri $url -ContentType "application/json" -Body $json2 | fl *;
```

