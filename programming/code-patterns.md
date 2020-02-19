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

### Async-Retry

Retry a promise until it's return value matches your expectations.

{% tabs %}
{% tab title="TypeScript" %}
```typescript
async function retrier<T>(
    promise: Promise<T>,
    checkFn: ValFunc<T>,
    maxRequests: number,
    waitTime: number,
    attempts = 0
): Promise<T> {
    if (++attempts > maxRequests) {
        throw new Error("Max attempts tried.");
    }
    // Await some request:
    var ret = await promise;
    if (!checkFn(ret)) {
        await delay(waitTime);
        return retrier(promise, checkFn, maxRequests, waitTime, attempts);
    }
    return Promise.resolve(ret);
}
type ValFunc<T> = (value: T) => boolean;
async function delay(milliseconds: number): Promise<void> {
    return new Promise<void>(resolve => setTimeout(resolve, milliseconds));
}
```
{% endtab %}
{% endtabs %}

