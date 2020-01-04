# Windows Registry

## Disable Downloaded File Blocking

```text
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Attachments]
"SaveZoneInformation"=dword:00000001
```

## Disable thumbs.db cache

```text
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]
"DisableThumbnailCache"=dword:00000001
[HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Explorer]
"DisableThumbsDBOnNetworkFolders"=dword:00000001
```

## Enable Hex Numpad

Doesn't seem to work for hex codes containing A-F.. 😒

```text
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Control Panel\Input Method]
"EnableHexNumpad"="1"
```

**Source**: [http://www.fileformat.info/tip/microsoft/enter\_unicode.htm](http://www.fileformat.info/tip/microsoft/enter_unicode.htm)

## Hide compressed icon

```text
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Shell Icons]
"179"="empty.ico,0"
```

## Hide git gui and shell context menu

```text
Windows Registry Editor Version 5.00
[HKEY_CLASSES_ROOT\Directory\Background\shell\git_gui]
"Extended"=""
[HKEY_CLASSES_ROOT\Directory\Background\shell\git_shell]
"Extended"=""
[HKEY_CLASSES_ROOT\Directory\shell\git_gui]
"Extended"=""
[HKEY_CLASSES_ROOT\Directory\shell\git_shell]
"Extended"=""
```

## IE allow dragndrop images to desktop

```text
[HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\Zones\4]
"180B"=dword:00000000
```

Then go into Internet Options &gt; Security and change ANYTHING and press apply. 

**Source**: [http://superuser.com/questions/52735/](http://superuser.com/questions/52735/drag-and-drop-images-from-a-webpage-into-a-local-folder)

