# Javascript

## Javascript

### Useful npm packages and tools

| Package | Description |
| :--- | :--- |
| npx | Run any npm tool without installing it: `npx cowsay hi` Run locally installed commands from the command line without creating a npm script: `npm -c "parcel index.html"` |
| nwjs | Run nodejs websites as desktop apps. In a standalone chrome browser. `nw index.html` runs the document as a server, so no blocked javascript from the `file://` protocol. |
| svgo | Optimize SVG files. |
| parcel-bundler | Fast, no-configuration bundler. |
| http-server | Webserver thats perfect for local testing: `npx http-server -a localhost -p 8080` |
| live-server | Webserver with live reload: Refreshes itself when you modify files. **Drawback**: Uses `=` before values in the command line argument, which I always forget. `npx live-server --port=80` |

## Node modules

### Node module template

```text
<className>.js
var <ClassName> = function() {};
<ClassName>.prototype.<methodName> = function(a) { return a; };
module.exports = <ClassName>;
```

How to use in other files

```text
var <ClassName> = require('./<className>');
<ClassName>.<methodName>('a');  //Returns the string 'a'.
```

Local modules are included like paths, but the file extension \(.js\) is optional. Node modules are included using its friendly name:

```text
require('fs');  //Includes the node module 'fs'
```

### Types

#### Error types

ECMA-262, 3rd Edition actually specifies seven error object types. These are used by the JavaScript engine when various error conditions occur and can also be manually created:

| Type | Description |
| :--- | :--- |
| Error | base type for all errors. Never actually thrown by the engine. |
| EvalError | thrown when an error occurs during execution of code via eval\(\). |
| RangeError | thrown when a number is outside the bounds of its range. For example, trying to create an array with -20 items \(new Array\(-20\)\). These occur rarely during normal execution. |
| ReferenceError | thrown when an object is expected but not available, for instance, trying to call a method on a null reference. |
| SyntaxError | thrown when the code passed into eval\(\) has a syntax error. |
| TypeError | thrown when a variable is of an unexpected type. For example, new 10 or "prop" in true. |
| URIError | thrown when an incorrectly formatted URI string is passed into encodeURI, encodeURIComponent, decodeURI, or decodeURIComponent. |

**Create your own error type that inherits from Error**

```text
function MyError(message){
    this.message = message;
}
MyError.prototype = new Error();
throw new MyError("Hello world!");
```

### Storage

#### Localstorage, calculate size

Source: [http://stackoverflow.com/questions/11613604/how-to-get-total-html5-storage-size-used-by-current-application](http://stackoverflow.com/questions/11613604/how-to-get-total-html5-storage-size-used-by-current-application)

Size:

```text
unescape(encodeURIComponent(JSON.stringify(localStorage))).length
```

Remaining size:

```text
var limit = 1024 * 1024 * 5; // 5 MB
var remSpace = limit - unescape(encodeURIComponent(JSON.stringify(localStorage))).length;
```

