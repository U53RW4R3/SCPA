# CPP

Search Tag(s): #command-line #compiler #windows

## 01 - Mingw

### 1.1 - Linux

#### 1.1.1 - EXE

- x86 architecture

```
$ i686-w64-mingw32-g++ implant.cpp -o implant.exe -lws2_32 -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc
```

- x86_64 architecture

```
$ x86_64-w64-mingw32-g++ implant.cpp -o implant.exe -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive
```

`$ clang++ -target x86_64-pc-windows-gnu implant.cpp -o implant.exe`

`$ zig c++ --target=x86_64-windows-gnu  -static implant.cpp -o implant.exe`

#### 1.1.2 - DLL

- x86 architecture

```
$ i686-w64-mingw32-g++ implant.cpp -o implant.dll -shared -lws2_32 -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc
```

- x86_64 architecture

```
$ x86_64-w64-mingw32-g++ implant.cpp -o implant.dll -shared -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive
```

### 1.2 - Linux

#### 1.2.1 - EXE

- x86_64 architecture

```
C:\> g++ implant.cpp -o implant.exe -s -static -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive
```

#### 1.2.2 - DLL

- x86_64 architecture

```
C:\> g++ implant.cpp -o implant.dll -shared -s -static -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive
```

## 02 - CL

- Compile Windows binaries in Windows

```
C:\> cl.exe /W4 /EHsc /Tpimplant.cpp /link /out:implant.exe /subsystem:console /machine:x64

C:\> cl.exe /nologo /0x /W0 /GS- /DNDEBUG /Tpimplant.cpp /link /out:implant.exe /subsystem:console /machine:x64
```