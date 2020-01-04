---
description: >-
  AWK is a domain-specific language designed for text processing and typically
  used as a data extraction and reporting tool. It is a standard feature of most
  Unix-like operating systems.
---

# AWK

## String replacement

List my environment paths in linux with linebreaks:

```bash
    echo $PATH | awk '{gsub(/\:/,"\n",$0); print}'
```

