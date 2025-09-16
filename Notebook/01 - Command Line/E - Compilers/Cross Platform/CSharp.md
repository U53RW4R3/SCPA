---
author(s):
  - Userware
tags:
  - helpers
  - command-line
  - compiler
  - dotnet
  - cross-platform
---
# CSharp

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

#### 1.2.1 - EXE Executable

Compile C# Project of Windows executable

> [!INFO] File Size
> Running the `-p:PublishSingleFile=true` flag will make the static .NET binary more than 60 MB which causes a practical problem for phishing scenarios. Be sure to use `-p:PublishTrimmed=true` to reduce the size.

```
> dotnet publish [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true

> dotnet publish [/path/to/project/] -r win10-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true

> dotnet publish [/path/to/project/] -f net6.0 -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true
```

Or you can just use `build`.

```
> dotnet build [/path/to/project/] -r win-x64 -c Release [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:PublishTrimmed=true

> dotnet build [/path/to/project/] -r win-x64 -c Release [-p:AllowUnsafeBlocks=true] -p:PublishSingleFile=true -p:AllowUnsafeBlocks=true -p:PublishTrimmed=true
```

> [!INFO] File Size
> Another way is to use `CoreRT` to reduce the static binary drastically at a minimum of 5 MB.

```
> dotnet publish [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:CoreRT

> dotnet publish [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:CoreRT-Moderate

> dotnet publish [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:CoreRT-High
```

#### 1.2.1 - DLL Executable

Create and Compile C# DLL

```
> dotnet new classlib [-o <project_name>]

> dotnet publish [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishTrimmed=true

> dotnet build [/path/to/project/] -r win-x64 -c Release --sc false [-p:AllowUnsafeBlocks=true] -p:PublishTrimmed=true
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

Add the repository.

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

#### 2.1.2 - Universal Installation

Install required dependencies depending your package manager.

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
$ mcs [-unsafe-] -sdk:<2 | 4 | 4.5> -out:payload.exe [-recurse:*.cs] Program.cs
```

Compile a `.dll` binary.

```
$ mcs [-unsafe-] -sdk:<2 | 4 | 4.5> -target:library -out:payload.dll [-recurse:*.cs] Program.cs
```

---
## References

### Microsoft

- [.NET Framework 4.8.1 version](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481)

### Source Repositories

- [WineHQ: Mono](https://gitlab.winehq.org/wine-mono/mono)

### Pentestlab

- [Pentestlab Blog: Applocker Bypass Assembly Load](https://pentestlab.blog/2017/06/06/applocker-bypass-assembly-load/)