# Node Module Template

```javascript
<className>.js
var <ClassName> = function() {};
<ClassName>.prototype.<methodName> = function(a) { return a; };
module.exports = <ClassName>;
```

How to use in other files

```javascript
var <ClassName> = require('./<className>');
<ClassName>.<methodName>('a');  //Returns the string 'a'.
```

Local modules are included like paths, but the file extension \(.js\) is optional. Node modules are included using its friendly name:

```javascript
require('fs');  //Includes the node module 'fs'
```

