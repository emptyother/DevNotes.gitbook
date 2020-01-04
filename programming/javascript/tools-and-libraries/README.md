---
description: Useful tools and libraries.
---

# Tools & Libraries

##  Tools

Can be useful to install globally \(`npm i -g`\). Or into your project \(`npm i --save-dev`\) if you only need the tool for that project.

| Package | Description |
| :--- | :--- |
| npx | Run any npm tool without installing it: `npx cowsay hi` Run locally installed commands from the command line without creating a npm script: `npm -c "parcel index.html"` |
| nwjs | Run nodejs websites as desktop apps. In a standalone chrome browser. `nw index.html` runs the document as a server, so no blocked javascript from the `file://` protocol. |
| svgo | Optimize SVG files. |
| parcel-bundler | Fast, no-configuration bundler. |
| http-server | Webserver thats perfect for local testing: `npx http-server -a localhost -p 8080` |
| live-server | Webserver with live reload: Refreshes itself when you modify files. **Drawback**: Uses `=` before values in the command line argument, which I always forget. `npx live-server --port=80` |

## Libraries

Install these to your npm project \(`npm i` or `npm i --save-dev`\).

| Package | Description |
| :--- | :--- |
| express | Basic webserver. |
| electron-prebuilt | Desktop web-app framework. |
| azure-storage | Azure Storage library. |

