---
description: Anything related to Windows Subsystem For Linux.
---

# Windows Subsystem For Linux

## How to Set Your Default Linux Distribution

To list all WSL systems installed:

```bash
wslconfig /l
```

To set one of them as default:

```bash
wslconfig /setdefault Name
```

### Set language

```bash
sudo update-locale LANG=en_US.UTF8
```

**Source**: [http://superuser.com/questions/1108090/](http://superuser.com/questions/1108090/how-do-i-change-the-language-of-the-linux-subsystem-in-windows-10-wsl)

### 

