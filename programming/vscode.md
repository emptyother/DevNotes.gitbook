---
description: >-
  Anything related to VSCode, Microsoft new light-weight cross-platform code
  editor. Look elsewhere for Visual Studio.
---

# Visual Studio Code

## VSCode wont run debugging

You've created a VSCode .Net Core console project, added the .Net Core debugger and added a breakpoint. But debugging gives this error:

```text
.pdb' is a Windows PDB. These are not supported by the cross-platform .NET Core debugger.
```

Solution: Add the following line to project.json, inside "buildOptions":

```text
"debugType": "portable"
```

