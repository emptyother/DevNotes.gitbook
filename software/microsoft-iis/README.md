---
description: Tips related to Microsoft IIS.
---

# Microsoft IIS

## C\# and Classes

### Static Classes

IIS creates only one instance of a static class per IIS application pool. Can't be an IDisposable \(for obvious reasons\).

### Instance Class

If its not a static class, its meant to be used as an instance using the "New" keyword.

### IDisposable

Instance Classes should implement IDisposable if it loads any resources \(database connections, open files, other IDisposables\). If you use a class that implements IDisposable, you should use a Using block for it. If not, no need.

### Singleton Class

Singleton Class is a Instance where the created instance is saved in a static property in the non-static class. Good for when you know the resources it loads wont change while the application is running, but you need to dispose of them afterwards. 

**Source**: [http://csharpindepth.com/Articles/General/Singleton.aspx](http://csharpindepth.com/Articles/General/Singleton.aspx)

