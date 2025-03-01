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

Clone the repository and compile the implant.

```
$ git clone https://github.com/int0x33/nc.exe.git && cd nc.exe/ && \
rm *.exe && sed -i -e s/\#CC=x86_64-pc-mingw32-gcc// \
-e s/\CC=i686-pc-mingw32-gcc/CC=x86_64-w64-mingw32-gcc/ Makefile && \
make 2>/dev/null
```

It's ready to be deployed as an implant.

```
$ file nc.exe 
nc.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
```

---
## References

### Source Repositories

- [int0x33: `nc.exe`](https://github.com/int0x33/nc.exe)