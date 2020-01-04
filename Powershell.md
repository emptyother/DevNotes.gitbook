# Powershell

## Using Regex

```powershell
$yourTextualOutput | % { $_ -match '^.*\\(.*)$' | Out-Null; $matches[1] }
```

## Creating Symlinks or Hardlinks or junctions

```powershell
New-Item -ItemType HardLink -Name github.js -Target ..\github.js
```

Notes:

- Creating symlinks require administrator privileges.
- Git can read hard links fine.
