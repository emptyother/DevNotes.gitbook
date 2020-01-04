---
description: WSL problems and solutions..
---

# Troubleshooting

## Cannot resolve local machine name

`sudo` on Windows 10 Linux subsystem cannot resolve local machine name.

### Solution

\[...\] remove `/etc/hosts` and restart bash to generate a version that contains your hostname. For me, it created a line with my computer name and my fully qualified name: `127.0.0.1 fbc-2000.domain.local fbc-2000`

**Source**: [https://superuser.com/questions/1108197/](https://superuser.com/questions/1108197/)

