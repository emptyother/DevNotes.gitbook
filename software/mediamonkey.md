---
description: A digital media player and media library application.
---

# MediaMonkey

## Retrieved lyrics get html tag codes in them

The lyricssearch is done by the java script "lyricsSearch.js" in the scripts folder. Inside the method "cleanupLyrics" there is these lines \(around line 273\):

```javascript
l = l.replace(/<\/?[^br>]+(>|$)+/gi, ''); // All other HTML tags that isn't <br>
l = l.replace(/<script>.*<\/script>/gi, ''); // remove script part added by LyricWikia, #12146
```

Modified them to this:

```javascript
l = l.replace(/<([A-Z][A-Z0-9]*)\b[^>]*>(.*?)<\/\1>/gi, ''); // All other HTML tags
l = l.replace(/<\/?[^br>]+(>|$)+/gi, ''); // All other HTML **end** tags that isn't <br>
l = l.replace(/<script>.*<\/script>/gi, ''); // remove script part added by LyricWikia, #12146
```

## Error: Type mismatch: 'CDbI'

Error - Microsoft VEScript runtme error Type mismatch: 'CDbI' File: 'C:LlserslTomAndreIAppDataBoamingWediaMonkeyEcriptsD'scogsAutoTagWeb.vbs., Line: 7197, Column: 4

Solution: File: %userprofile%\AppData\Roaming\MediaMonkey\Scripts\DiscogsAutoTagWeb.vbs Line: 7197 Replace: ParseValue = CDbl\(ms\(0\)\) With: ParseValue = CDbl\(Replace\(ms\(0\),".",","\)\)

## Auto-Organize Path for sorting into a Onedrive music folder

```markup
.\OneDrive\Music\<Album Artist>\<Album>\$If(<Disc#>,\Disc <Disc#>)\$If(<Track#>, <Track#> - )<Title>
```

