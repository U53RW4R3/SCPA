---
author(s):
  - Userware
tags:
  - helpers
  - command-line
  - compiler
  - python
  - cross-platform
---
# Python

> [!IMPORTANT]
> The selected compiler versions will not work against Windows XP and Windows Server 2003 including earlier versions.
> > [!NOTE]
> > This is subjected to change in the future due to different versions might be changed. We'll wait and see user.

## 01 - Installer Python Interpreter

### 1.1 - Directly From `wine`

This specific version works with Windows 8 and later. It also contains PIP installer.

```
$ wget https://www.python.org/ftp/python/3.11.6/python-3.11.6-amd64.exe
```

This specific version works with Windows 7 and later. It also contains PIP installer.

```
$ wget https://www.python.org/ftp/python/3.8.9/python-3.8.9-amd64.exe
```

Run the installer.

```
$ wine python-<version>-amd64.exe
```

Follow the instructions:
- Click **Custom Install**
- Click **Next** to move on **Advanced Options**
- Click **install for all users** (check the destination if it's `C:\Program Files\Python38`)
- Click **Add Python to environment variables**.
- Click **Install**.

### 1.2 - Docker Container

This is another option if you prefer for the latest version of python windows binary. Pull the latest tag.

```
$ docker pull tobix/pywine:latest
```

This specific version works with Windows 8 and later. It also contains PIP installer.

```
$ docker pull tobix/pywine:3.11.6
```

This specific version works with Windows 7 and later. It also contains PIP installer.

```
$ docker pull tobix/pywine:3.8.9
```

Interact the docker container. Keep in mind this won't work on legacy Windows operating systems such as, Windows XP, 7, Windows Server 2003 and so on.

```
$ docker run --rm -it --entrypoint /bin/bash tobix/pywine
```

## 02 - Cross Compile Windows

### 1.1 - `nuitka`

Install `nuitka` and `mfc42.dll`dependency. 

```
$ wine python -m pip install nuitka

$ winetricks -q mfc42
```

You can now cross-compile the python (`.py`) files into windows executable files (`.exe`). Don't worry about the error message `depends.exe`. It should be compiled if you check.

```
$ WINEDEBUG=-all wine cmd.exe /c nuitka [--windows-icon-from-ico file.ico | --windows-icon-from-exe "/path/to/program.exe"] [--follow-imports] --standalone --onefile payload.py

$ WINEDEBUG=-all wine python -m nuitka [--windows-icon-from-ico file.ico | --windows-icon-from-exe "/path/to/program.exe"] [--follow-imports] --standalone --onefile payload.py

$ docker run -v $(pwd):/tmp tobix/pywine WINEDEBUG=-all wine python -m nuitka [--windows-icon-from-ico file.ico | --windows-icon-from-exe "/path/to/program.exe"] [--follow-imports] --standalone --onefile --output-dir=/tmp/ /tmp/payload.py

$ file payload.dist/payload.exe 
payload.dist/payload.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
```

### 1.2 - `pyinstaller`

For docker it is already preinstalled so you can skip it.

```
$ wine python -m pip install pyinstaller
```

You can now cross-compile the python (`.py`) files into windows executable files (`.exe`).

```
$ WINEDEBUG=-all wine pyinstaller [-i file.ico] -F -w payload.py

$ docker run -v $(pwd):/tmp tobix/pywine WINEDEBUG=-all wine pyinstaller [-i file.ico] -F -w /tmp/payload.py --distpath /tmp/dist

$ file dist/payload.exe 
dist/payload.exe: PE32+ executable (GUI) x86-64, for MS Windows
```

---
## References

- [Python](https://python.org)

- [Nuitka](https://nuitka.net/)

- [Pyinstaller](https://pyinstaller.org/en/stable/)

- [webcomics: pywine](https://github.com/webcomics/pywine)

- [MakeWorld: How to create Windows EXEs for Python on Linux, using PyInstaller and WINE](https://www.makeworld.space/2021/10/linux-wine-pyinstaller.html)

- [Threat.Zone: Create More Complicated Binaries with Nuitka & LLVM-Obfuscator](https://blog.threat.zone/create-more-complicated-binaries-with-nuitka-llvm-obfuscator/)