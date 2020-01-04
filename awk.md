# AWK

## String replacement

List my environment paths in linux with linebreaks:

```bash
    echo $PATH | awk '{gsub(/\:/,"\n",$0); print}'
```
