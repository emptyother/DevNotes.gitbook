---
description: 'Anything related to JavaScript, NodeJS, TypeScript, and NPM.'
---

# Javascript

## Storage

### Localstorage, calculate size

**Source:** [http://stackoverflow.com/questions/11613604/](http://stackoverflow.com/questions/11613604/how-to-get-total-html5-storage-size-used-by-current-application)

Size:

```javascript
unescape(encodeURIComponent(JSON.stringify(localStorage))).length
```

Remaining size:

```javascript
var limit = 1024 * 1024 * 5; // 5 MB
var remSpace = limit - unescape(encodeURIComponent(JSON.stringify(localStorage))).length;
```

