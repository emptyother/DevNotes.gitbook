# Windows-Subsystem-For-Linux

## Windows-Subsystem-For-Linux

### How to Set Your Default Linux Distribution

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

Source: [http://superuser.com/questions/1108090/how-do-i-change-the-language-of-the-linux-subsystem-in-windows-10-wsl](http://superuser.com/questions/1108090/how-do-i-change-the-language-of-the-linux-subsystem-in-windows-10-wsl)

## Troubleshooting

### Cannot resolve local machine name

sudo on Windows 10 Linux subsystem cannot resolve local machine name

\[...\] remove /etc/hosts and restart bash to generate a version that contains your hostname. For me, it created a line with my computer name and my fully qualified name 127.0.0.1 fbc-2000.domain.local fbc-2000

Source: [superuser.com](http://superuser.com/questions/1108197/sudo-on-windows-10-linux-subsystem-cannot-resolve-local-machine-name?rq=1)

