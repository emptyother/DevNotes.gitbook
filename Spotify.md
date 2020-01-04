# Spotify

## Problem: Can't play this track

When playing local files, Spotify occasionally states "Can't play this track".
Various recommendations have been to turn off hardware acceleration, turn off
high quality streaming, turn off crossfade, but none of them worked.

Finally fixed it by going into the prefs file at
`%localappdata%\Packages\SpotifyAB.SpotifyMusic_zpdnekdrzrea0\LocalState\Spotify\Users\username-user\prefs`
and setting `audio.crossfade_v2=false` and `audio.crossfade.time_v2=0`. Somewhy
Spotify don't read these settings correctly so setting them in the "Preferences"
menu don't work.
