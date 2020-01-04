---
description: Useful AHK scripts.
---

# AutoHotKey scripts

## Repeatable mouse clicker

{% code title="MouseClicker.ahk" %}
```text
#NoEnv
#Warn
#SingleInstance force
SendMode Input

;F8 - Repeat mouse left click while this key is held down
F8::
	While GetKeyState("F8","P") {
		Click
		Sleep 50
	}
Return

```
{% endcode %}

## Paste UTC DateTime

{% code title="PasteUTCDateTime.ahk" %}
```text
#NoEnv
#Warn
#SingleInstance force
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.

;Win+V - Paste UTC DateTime stamp
<#v::
	FormatTime, xx, %A_NowUTC%, yyyyMMddTHHmmssZ
	SendInput, %xx%
Return
```
{% endcode %}

