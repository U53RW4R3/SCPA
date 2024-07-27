# C

Search Tag(s): #command-line #compiler #windows

## 01 - Mingw

- Setup `mingw-w64`

```
$ wget https://musl.cc/x86_64-w64-mingw32-cross.tgz && \
sudo tar xzf x86_64-w64-mingw32-cross.tgz -C /usr/local/ && \
echo "export PATH=\$PATH:/usr/local/x86_64-w64-mingw32-cross/bin" >> ~/.bashrc && \
source ~/.bashrc
```

- Compile Windows binaries in Linux

```
$ i686-w64-mingw32-gcc implant.c -o implant_x86.exe

$ x86_64-w64-mingw32-gcc implant.c -o implant.exe

$ clang -target x86_64-pc-windows-gnu implant.c -o implant.exe

$ zig cc --target=x86_64-windows-gnu -static implant.c -o implant.exe
```

- Compile Windows binaries in Linux with icons

```
$ x86_64-w64-mingw32-windres resource.rc resource.o

$ x86_64-w64-mingw32-gcc -o implant.exe resource.o implant.c
```

- Compile Windows Dynamic Linked Library in Linux

```
$ i686-w64-mingw32-gcc implant-x86.c -shared -o implant-x86.dll

$ x86_64-w64-mingw32-gcc implant-x86_64.c -shared -o implant-x86_64.dll
```

## 02 - CL

- Compile Windows binaries

```
C:\> cl.exe /W4 /EHsc implant.c /link /out:implant.exe
```

- Compile Windows Dynamic Linked Library

TODO: Fill this info

```
C:\>
```

- Compile Windows binaries with icons

```
C:\> rc resource.rc

C:\> cvtres /machine:x64 /out:resource.o resource.res

C:\> cl.exe /nologo /0x /W0 /GS- /DNDEBUG /Tcimplant.c /link /out:implant.exe /subsystem:console /machine:x64 resource.o
```

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