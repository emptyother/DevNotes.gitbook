---
description: >-
  ECMA-262, 3rd Edition actually specifies seven error object types. These are
  used by the JavaScript engine when various error conditions occur and can also
  be manually created.
---

# Error Types

| Type | Description |
| :--- | :--- |
| Error | Base type for all errors. Never actually thrown by the engine. |
| EvalError | Thrown when an error occurs during execution of code via eval\(\). |
| RangeError | Thrown when a number is outside the bounds of its range. For example, trying to create an array with -20 items \(new Array\(-20\)\). These occur rarely during normal execution. |
| ReferenceError | Thrown when an object is expected but not available, for instance, trying to call a method on a null reference. |
| SyntaxError | Thrown when the code passed into eval\(\) has a syntax error. |
| TypeError | Thrown when a variable is of an unexpected type. For example, new 10 or "prop" in true. |
| URIError | Thrown when an incorrectly formatted URI string is passed into encodeURI, encodeURIComponent, decodeURI, or decodeURIComponent. |

## **Create your own error type**

```javascript
function MyError(message){
    this.message = message;
}
MyError.prototype = new Error();
throw new MyError("Hello world!");
```

