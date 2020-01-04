---
description: >-
  In software engineering, a software design pattern is a general, reusable
  solution to a commonly occurring problem within a given context in software
  design.
---

# Code Patterns

### Singleton

A class with a private constructor. Then how do you call the constructor? By calling a public method within the constructor which cakes the constructor \(if necessary\) and then returns itself.

{% tabs %}
{% tab title="C\#" %}
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
{% endtab %}

{% tab title="C\# Thread-safe" %}
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
{% endtab %}
{% endtabs %}

