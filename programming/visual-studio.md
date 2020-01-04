# Visual Studio

## Where is Visual Studio's "browse with..." list saved?

```text
%localappdata%\Microsoft\VisualStudio\14.0\browsers.xml
```

## Could not load file or assembly PageInspector

Source: [http://stackoverflow.com/questions/21829419/could-not-load-file-or-assembly-microsoft-visualstudio-web-pageinspector-loader](http://stackoverflow.com/questions/21829419/could-not-load-file-or-assembly-microsoft-visualstudio-web-pageinspector-loader)

I just ran into the same problem, and the culprit was my uninstalling of Visual Studio Express 2012. \(Possible that it might be any version of VS2012.\) My overall order of operations was:

1. Installed Visual Studio Express 2012 \(long time ago\)
2. Used Visual Studio Express 2012 happily for many months
3. Installed Visual Studio 2013 Premium
4. Used Visual Studio 2013 Premium happily for weeks
5. Uninstalled Visual Studio Express 2012
6. ERROR

I'm not 100% certain on the cause of it, or what combinations of VS 2012/2013 would exhibit this behavior. But the solution for me was to edit the root web.config in the framework directory: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\Config\web.config`. And remove the lines:

```markup
<remove assembly="Microsoft.VisualStudio.Web.PageInspector.Loader, Version=1.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />
<add assembly="Microsoft.VisualStudio.Web.PageInspector.Loader, Version=1.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />
```

This resolved the issue for me.

## Entity Framework error

**Error:** System.Data.Entity.Core.MappingException: The type 'Edm.Boolean' does not match with the type System.Int32 on the object side

**Solution:** EF doesnt like having two tables/objects with the same name in two different databases, even if the table isnt included in the database model. Fixed it by moving one of the database object definition \(\*.edmx\) into another project.

## Requested registry access is not allowed

Source: [http://support2.microsoft.com/kb/842795](http://support2.microsoft.com/kb/842795)

If you log on to a computer as a regular user, and if you try to use Microsoft Visual Studio .NET to create a custom event log to register events, you may receive the following error message:

```text
An unhandled exception of type 'System.Security.SecurityException' occurred in mscorlib.dll
Additional information: Requested registry access is not allowed.
```

This problem occurs because the user account that you used to log on does not have sufficient permissions.

The first time that you call the EventLog.CreateEventSource\(\) method to create a custom event log, the custom event log entry is created under the following registry subkey:

```text
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Eventlog
```

To create this subkey entry, you must have permission to write. However, the regular user account does not have permission to write. Therefore, you receive the error message that is mentioned in the "Symptoms" section.

Didn't work, so here's the working solution

```text
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog\
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog\Security
```

La fulle rettigheter til disse nøklene for brukerne "Authenticated Users" og "Network Service". Jeg får finne ut hvem av dem som FAKTISK fungerte. Originalt så hadde Authenticated Users kun rettighet til å lese eventlog og Network Service eksisterte ikke på noen.

## MsBuild

### Build .NET 4.7 apps

Having trouble getting msbuild to build a .NET 4.7 package?

1. Install dotnet 4.7: `cinst dotnet4.7 -y`
2. Install dotnet 4.7 targeting pack from either Visual Studio installer or this package: `bat cinst netfx-4.7-devpack -y`

