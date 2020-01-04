---
description: Troubleshoot IIS problems.
---

# Troubleshooting

## Page Inspector's Runtime must be installed in the Global Assembly Cache

Edit file:

```text
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config
C:\Windows\Microsoft.NET\Framework\v4.0.30319\Config\web.config
```

Add line:

_..Missing text.. Sorry._

## Unable to access the IIS metabase

If you want access to the IIS metabase while running Visual Studio not as administrator, you need to give yourself access to these folders:

* `%systemroot%\inetsrv\config`
* `%systemroot%\inetsrv\config\Export`

**Source**: [stackoverflow.com](https://stackoverflow.com/questions/12859891/error-unable-to-access-the-iis-metabase)

## Application Pool wont start

```text
The worker process for application pool 'DefaultAppPool' encountered an error 'Cannot read configuration file
' trying to read configuration data from file '\\?\<EMPTY>', line number '0'.
```

If you've deleted and created a new "DefaultAppPool", it will stop when trying to read the configs. Create a new AppPool that isn't named "DefaultAppPool".

