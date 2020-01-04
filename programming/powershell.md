---
description: Anything related to Powershell.
---

# PowerShell

## Output from Start-Process

Use the `-NoNewWindow -Wait` parameters.

## Using Regex

```bash
$yourTextualOutput | % { $_ -match '^.*\\(.*)$' | Out-Null; $matches[1] }
```

## Creating Symlinks or Hardlinks or junctions

```bash
New-Item -ItemType HardLink -Name github.js -Target ..\github.js
```

Notes:

* Creating symlinks require administrator privileges.
* Git can read hard links fine.

