# Troubleshooting

### Cannot resolve local machine name

**Problem**: `sudo` on Windows 10 Linux subsystem cannot resolve local machine name.

\[...\] remove `/etc/hosts` and restart bash to generate a version that contains your hostname. For me, it created a line with my computer name and my fully qualified name: `127.0.0.1 fbc-2000.domain.local fbc-2000`

**Source**: [superuser.com](http://superuser.com/questions/1108197/sudo-on-windows-10-linux-subsystem-cannot-resolve-local-machine-name?rq=1)
