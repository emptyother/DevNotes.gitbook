---
description: Tips for doing LINQ queries.
---

# LINQ

## Chaining Where's

LINQ does a fair bit of optimizing at runtime, and all this will be wasted if you dont: 

```csharp
// Good, or bad if MySQL (see below)
    .Where(p1==4)
    .Where(p2==5)
// Bad, or good if MySQL (see below)
    .Where(p1==4 && p2==5)
```

### ⚠ WARNING

I've noticed that _chaining where's_ **is really bad** against MySQL when querying navigational properties. Better to be on the safe side and don't chain them when querying MySQL.

## LINQ is lazy

If you do stuff like `list.Where(a => a=1).First()`, it will not query everything and only return one. It will optimize it before doing the query so the work would be the same as if you did `list.First(a => a=1)`.



