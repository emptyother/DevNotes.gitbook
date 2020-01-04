# Code Patterns

### Singleton

A class with a private constructor. Then how do you call the constructor? By calling a public method within the constructor which cakes the constructor \(if necessary\) and then returns itself.

[http://csharpindepth.com/Articles/General/Singleton.aspx](http://csharpindepth.com/Articles/General/Singleton.aspx)

```csharp
    public sealed class Singleton
    {
        private static Singleton instance = null;
        private static readonly object padlock = new object();

        Singleton()
        {
        }

        public static Singleton Instance
        {
            get
            {
                lock (padlock)
                {
                    if (instance == null)
                    {
                        instance = new Singleton();
                    }
                    return instance;
                }
            }
        }
    }
```

Or cleaner:

```csharp
    public sealed class Singleton
    {
        private static readonly Singleton instance = new Singleton();

        // Explicit static constructor to tell C# compiler
        // not to mark type as beforefieldinit
        static Singleton()
        {
        }

        private Singleton()
        {
        }

        public static Singleton Instance
        {
            get
            {
                return instance;
            }
        }
    }
```

