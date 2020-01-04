---
description: Anything related to Node Package Manager.
---

# Node Package Manager

## Useful Commands

| Command | Comment |
| :--- | :--- |
| npm install | Installs all required packages to current project |
| npm install \[packagename\] | Install a single package to current project |
| npm install -g \[packagename\] | Installs a single package to the computer |
| npm init | Wizard to set up the package.json file |

| Package name | Install scope | Description |
| :--- | :--- | :--- |
| express | proj | Basic webserver |
| electron-prebuilt | -g | Desktop web-app framework |
| azure-storage | proj | Azure Storage |

## Useful node.js included modules

Include by using require\('\[moduleName\]'\);

| Module name | Description |
| :--- | :--- |
| fs | Reading file system |
| http | Very basic webserver |
| url | Url reader utility? |
| util | util.inspect\(obj\) is like var\_dump\(obj\) from php. |

```text
<className>.js
var <ClassName> = function() {};
<ClassName>.prototype.<methodName> = function(a) { return a; };
module.exports = <ClassName>;
var <ClassName> = require('./<className>');
<ClassName>.<methodName>('a');  //Returns the string 'a'.
```

Local modules are included like paths, but the file extension \(.js\) is optional. Node modules are included using its friendly name: require\('fs'\); //Includes the node module 'fs'

## Package.json

See more details here: [https://docs.npmjs.com/files/package.json](https://docs.npmjs.com/files/package.json)

File example:

```text
{
    "name": "nodetut",
    "version": "1.0.0",
    "description": "Node tutorial",
    "main": "main.js",
    "dependencies": {
        "express": "4.13.x"
    },
    "devDependencies": {},
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "",
    "license": "ISC",
    "private": true,
    "repository": {
        "type": "",
        "url": ""
    }
}
```

### Name

Required!

### Version

### Description

Required!

### Main

Mainfile for the project.

### Dependencies

List of packages that will be automaticly installed when running "npm install".

### DevDependencies

### Scripts

Scripts to run for testing. Or for other stuff.

### Docs:

[https://docs.npmjs.com/misc/scripts](https://docs.npmjs.com/misc/scripts)

### Author

### License

Default is "ISC".

### Private

Set to "true" if its not supposed to be published. If its true, the field "Repository" is no longer required.

### Repository

Partial required! See "Private".

**Docs:**

* [http://stackoverflow.com/questions/16827858/npm-warn-package-json-no-repository-field](http://stackoverflow.com/questions/16827858/npm-warn-package-json-no-repository-field)
* [https://docs.npmjs.com/files/package.json\#repository](https://docs.npmjs.com/files/package.json#repository)

### Type

Can be:

* svn
  * url: svnurl
* git
  * url: giturl
* npm/npm
* gist:\(gistid\)
* bitbucket:example/repo
* gitlab:another/repo

```text
npm ls -g --depth=0 --parseable | % { $_ -match '^.*\\(.*)$' | Out-Null; $matches[1] } | Out-File npm-packages.txt
```

