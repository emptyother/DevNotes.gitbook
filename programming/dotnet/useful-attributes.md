---
description: 'List of useful attributes found in C#.'
---

# Useful attributes

## Misc

### ObsoleteAttribute

Mark a method, class or whatever as obsolete.

### SerializableAttribute

Mark a class as serializable for Microsofts json serializer.

### FlagsAttribute

Used on enums to mark them as flaggable \(that you can have multiple enum values\). The enum values should be a multiple of 2. I recommend you mark 0 as none and -1 as all, because of the way bits work.

```csharp
[Flags]
enum AllowPet {
    All = -1,
    None = 0,
    Cat = 1,
    Dog = 2,
    Fish = 4,
    Lizard = 8
}
AllowPet petsAllowed = Allow.Cat | Allow.Fish;
// petsAllowed is now 5
```

## Newtonsoft.JSON

### JsonIgnoreAttribute

Dont serialize this property.

## Debugging

### ConditionalAttribute

Only run this method if we are debugging. Any calls to it while in production is just ignored.

Only works on methods that doesnt return anything.

```csharp
// Dont run this method unless we are debugging
[System.Diagnostics.Conditional("DEBUG")]
public void LogDebugging(string text) {}
```

### DebuggerStepThroughAttribute

Instructs the debugger to step through the code instead of stepping into the code. Ignores breakpoints. Will be shown as "external code" in call stack.

```csharp
[DebuggerStepThrough]
public void LogDebugging(string text) {}

// DebuggerHiddenAttribute is the same,
// but even hides it from the call stack.
[DebuggerHidden]
public void LogDebugging(string text) {}
```

### DebuggerTypeProxyAttribute

Use another class to generate the debugger view. Useful to only show certain values when debugging.

```csharp
internal class UserDebuggerView {
    private User BaseUser { get; set; }
    public UserDebuggerView(User user) {
        this.BaseUser
    }
    public int Fullname {
        get {
            return this.BaseUser.Firstname + this.BaseUser.Lastname;
        }
    }
}
[DebuggerTypeProxy(typeof(MyDebuggerView))]
public class User {}
```

## Web API

### PrincipalPermissionAttribute

Block users based on their roles, etc.

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = Scopes.Read)]
public async Task<User> GetUser(int id) {}
```

### RouteAttribute

```csharp
[RoutePrefix("api/users/")]
class UserController {
    [Route("GetUser/{id}")]
    public async Task<User> GetUser(int id) {}
    // Final route example: "api/users/GetUser/3"
}

```



