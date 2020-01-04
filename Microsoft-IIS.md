# Microsoft IIS

## Page Inspector's Runtime must be installed in the Global Assembly Cache

Edit file:

    C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config
    C:\Windows\Microsoft.NET\Framework\v4.0.30319\Config\web.config

Add line:

    <add assembly="Microsoft.VisualStudio.Web.PageInspector.Loader, Version=1.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />

## Unable to access the IIS metabase

If you want access to the IIS metabase while running Visual Studio not as
administrator, you need to give yourself access to these folders:

- `%systemroot%\inetsrv\config`
- `%systemroot%\inetsrv\config\Export`

Source:
[stackoverflow.com](https://stackoverflow.com/questions/12859891/error-unable-to-access-the-iis-metabase)

## Application Pool wont start

```log
The worker process for application pool 'DefaultAppPool' encountered an error 'Cannot read configuration file
' trying to read configuration data from file '\\?\<EMPTY>', line number '0'.
```

If you've deleted and created a new "DefaultAppPool", it will stop when trying
to read the configs. Create a new AppPool that isn't named "DefaultAppPool".

## IIS and Classes

### Static Classes

IIS creates only one instance of a static class per IIS application pool. Cant
be an IDisposable (for obvious reasons).

### Instance Class

If its not a static class, its meant to be used as an instance using the "New"
keyword.

### IDisposable

Instance Classes should implement IDisposable if it loads any resources
(database connections, open files, other IDisposables). If you use a class that
implements IDisposable, you should use a Using block for it. If not, no need.

### Singleton Class

Singleton Class is a Instance where the created instance is saved in a static
property in the non-static class. Good for when you know the resources it loads
wont change while the application is running, but you need to dispose of them
afterwards. http://csharpindepth.com/Articles/General/Singleton.aspx

... Need more investigation....
