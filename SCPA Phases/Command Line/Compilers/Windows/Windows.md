# Windows

Search Tag(s): #command-line #compiler #windows

## 01 - MASM

```
C:\> ml /c /coff shell.asm

C:\> link /SUBSYSTEM:WINDOWS /ENTRY:start /VERSION:4.0 shell.obj

C:\> objcopy -O binary shell.exe shell.bin
```

## 02 - C

### 2.1 - Cross Compilers

- Setup `mingw-w64`

```
$ wget https://musl.cc/x86_64-w64-mingw32-cross.tgz && \
sudo tar xzvf x86_64-w64-mingw32-cross.tgz -C /usr/local/ && \
echo "export PATH=\$PATH:/usr/local/x86_64-w64-mingw32-cross/bin" >> ~/.bashrc && \
source ~/.bashrc
```

- Compile Windows binaries in Linux

```
$ i686-w64-mingw32-gcc shellcode.c -o shell.exe

$ x86_64-w64-mingw32-gcc shellcode.c -o shell.exe

$ clang -target x86_64-pc-windows-gnu shell.c -o shell.exe

$ zig cc --target=x86_64-windows-gnu -static shell.c -o shell.exe
```

- Compile Windows binaries in Linux with icons

```
$ x86_64-w64-mingw32-windres resource.rc resource.o

$ x86_64-w64-mingw32-gcc -o shell.exe resource.o shell.c
```

- Compile Windows Dynamic Linked Library in Linux

```
$ i686-w64-mingw32-gcc shellcode.c -shared -o shell-x86.dll

$ x86_64-w64-mingw32-gcc shellcode.c -shared -o shell-x86_64.dll
```

### 2.2 - CL

- Compile Windows binaries

`C:\> cl.exe /W4 /EHsc shellcode.c /link /out:shellcode.exe`

- Compile Windows Dynamic Linked Library

TODO: Fill this info

`C:\>`

- Compile Windows binaries with icons

```
C:\> rc resource.rc

C:\> cvtres /machine:x64 /out:resource.o resource.res

C:\> cl.exe /nologo /0x /W0 /GS- /DNDEBUG /Tcshell.c /link /out:shell.exe /subsystem:console /machine:x64 resource.o
```

## 03 - C++

### 3.1 - Cross Compilers

- Compile Windows binaries in Linux

`$ i686-w64-mingw32-g++ shell.cpp -o shell.exe -lws2_32 -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc`

`$ x86_64-w64-mingw32-g++ shell.cpp -o shell.exe -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

`$ clang++ -target x86_64-pc-windows-gnu shell.cpp -o shell.exe`

`$ zig c++ --target=x86_64-windows-gnu  -static shell.cpp -o shell.exe`

- Compile Windows Dynamic Linked Library in Linux

`$ i686-w64-mingw32-g++ shell.cpp -o shell.dll -shared -lws2_32 -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc`

`$ x86_64-w64-mingw32-g++ shell.cpp -o shell.dll -shared -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

- Compile Windows binaries in Windows

`C:\> g++ shell.cpp -o shell.exe -s -static -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

- Compile Windows Dynamic Linked Library in Windows

`C:\> g++ shell.cpp -o shell.dll -shared -s -static -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

### 3.2 - CL

- Compile Windows binaries in Windows

`C:\> cl.exe /W4 /EHsc /Tpshell.cpp /link /out:shell.exe /subsystem:console /machine:x64`

`C:\> cl.exe /nologo /0x /W0 /GS- /DNDEBUG /Tpshell.cpp /link /out:shell.exe /subsystem:console /machine:x64`

---
## References

### Toolchains

- [musl.cc](https://musl.cc/)

- [Mingw-64 Toolchain (bleeding edge)](https://sourceforge.net/p/mingw-w64/)

- [Cross-compiling with musl Toolchains](https://ariya.io/2020/06/cross-compiling-with-musl-toolchains)

### Compiling Guides

- [Malicious.link: Compiling a DLL using MingGW](https://room362.com/posts/2020/compiling-a-dll-using-mingw/)

- [EDR and Blending In: How Attackers Avoid Getting Caught](https://www.optiv.com/insights/source-zero/blog/edr-and-blending-how-attackers-avoid-getting-caught)

- [Quickpost Compiling EXEs and Resources with Mingw on Kali](https://blog.didierstevens.com/2018/09/17/quickpost-compiling-exes-and-resources-with-mingw-on-kali/)

- [Zig C Compiler Powerful Drop in Replacment GCC Clang](https://andrewkelley.me/post/zig-cc-powerful-drop-in-replacement-gcc-clang.html)