---
description: Anything related to Windows Subsystem for Linux (WSL).
---

# Windows Subsystem for Linux

## How to Set Your Default Linux Distribution

To list all WSL systems installed:

```bash
wslconfig /l
```

To set one of them as default:

```bash
wslconfig /setdefault Name
```

### Set distro Language

```bash
sudo update-locale LANG=en_US.UTF8
```

**Source**: [http://superuser.com/questions/1108090/](http://superuser.com/questions/1108090/how-do-i-change-the-language-of-the-linux-subsystem-in-windows-10-wsl)

## Get a full Linux Desktop with WSL \(X Server setup\)

* [ ] **TODO**: _Rewrite this.._

**Source**: [Reddit](https://www.reddit.com/r/Windows10/comments/4ycxaz/the_new_linux_subsystem_is_pretty_good/)

Download Xming or any other X server. Launch bash and type in the following lines:

```bash
sudo apt-get install xorg xubuntu-desktop
echo 'export DISPLAY=:0' >> ~/.bashrc && . ~/.bashrc
sudo sed -i 's$<listen>.*</listen>$<listen>tcp:host=localhost,port=0</listen>$' /etc/dbus-1/session.conf
```

1. Close Bash and open it, then type in `xfce4-session` , if everything went right then the XFCE interface should show up in your X server window.
2. Then install Arc OSX Theme
3. And Super Flat Remix Icon Theme
4. Wallpaper

Edit: You can make a Virtual Desktop in Windows, & put the Xming window there then press Ctrl+Win+Right/Left to switch between Windows & Linux. Like this

Edit \#2: If you don't want Windows to manage the applications' wm. Close everything then open XLaunch \(not xming\), then select "One window without title bar", then keep pressing next until finish. After clicking finish, open Bash and type xfce4-session

Edit \#3: If Xming is slow try using VcXsrv

## Set up SSH Server

Edit `/etc/ssh/sshd_config`:

```bash
Port 60022 # Or anything not 22
ListenAddress 0.0.0.0
UsePrivilegeSeparation No
AllowUsers tom
PasswordAuthentication yes
PermitRootLogin no # Not needed but recommended.
```

Restart the ssh service: `service ssh --full-restart`

I also had to restart the services in windows \(SSH \*\).

