---
description: 'Troubles with my favorite laptop series, the Microsoft Surface Pro.'
---

# Surface Pro troubleshooter

## Slow network speed

Was a bug with Surface Pro 4. This has been fixed by Microsoft a long time ago, but just in case anyone needs it again, append this registry change:

```text
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\mrvlpcie8897]
"TxAMSDU"=dword:00000000
```

## Insert-key doesn't work

Pressing the `Ins` key on the Surface Pro keyboard only trigger a delete.

**Solution**: Hold the `Fn` key when you press `Del` to trigger a Insert. 



