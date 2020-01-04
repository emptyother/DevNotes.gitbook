---
description: 'It is not GIT''s fault, usually.'
---

# Troubleshooting

## Unable to to start 'ssh-agent.exe'

'ssh-agent' failed with code -1: System.Exception: Unable to to start 'ssh-agent.exe' check the git installation.

### Solution

```bash
rebase.exe -b 0x50000000 msys-1.0.dll
```

_I don't remember why this was the solution_.. Sorry.

