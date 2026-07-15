# CPP

Search Tag(s): #helpers #command-line #compiler #windows

## 01 - MinGW

### 1.1 - EXE

x86 architecture

```
$ i686-w64-mingw32-g++ payload.cpp -o payload.exe -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc
```

x86_64 architecture

```
$ x86_64-w64-mingw32-g++ payload.cpp -o payload.exe -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive
```

### 1.2 - DLL

x86 architecture

```
$ i686-w64-mingw32-g++ payload.cpp -o payload.dll -shared -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc
```

x86_64 architecture

```
$ x86_64-w64-mingw32-g++ payload.cpp -o payload.dll -shared -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive
```

## 02 - Clang

```
$ clang++ -target x86_64-pc-windows-gnu -O2 -o payload.exe payload.cpp

$ x86_64-w64-mingw32-clang++ -O2 -o payload.exe payload.c
```

## 03 - Zig

```
$ zig c++ --target=x86_64-windows-gnu -static payload.cpp -o payload.exe
```

## 04 - MSVC

Compile Windows binaries in Windows

```
C:\> cl.exe /W4 /EHsc /Tp payload.cpp /link /out:payload.exe /subsystem:console /machine:x64

C:\> cl.exe /nologo /0x /W0 /GS- /DNDEBUG /Tp payload.cpp /link /out:payload.exe /subsystem:console /machine:x64
```

---
## References

### Backlinks

- [[03 - Offensive Infrastructure/E - Setup Machine/0x01 - Essentials/Compilers/Windows/C|Windows Compilers: C]]