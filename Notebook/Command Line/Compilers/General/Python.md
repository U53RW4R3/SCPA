# Python

Search Tag(s): #command-line #compiler #python #linux #windows

Note: This is subjected to change in the future due to different versions might be changed. We'll wait and see user.

## 01 - Installer Python Interpreter

### 1.1 - Directly from `wine`

This specific version works with Windows 7 and later. It also contains PIP installer because other python versions doesn't come pre-bundled and it's impossible to install it.

```
$ wget https://www.python.org/ftp/python/3.8.9/python-3.8.9-amd64.exe
```

Run the installer.

```
$ wine python-3.8.9-amd64.exe
```

Follow the instructions:
- Click **Custom Install**
- Click **Next** to move on **Advanced Options**
- Click **install for all users** (check the destination if it's `C:\Program Files\Python38`)
- Click **Add Python to environment variables**.
- Click **Install**.

### 1.2 - Docker container

This is another option if you prefer for the latest version of python windows binary. Pull the latest tag.

```
$ docker pull tobix/pywine:latest
```

Interact the docker container. Keep in mind this won't work on legacy Windows operating systems such as, Windows XP, 7, Windows Server 2003 and so on.

```
$ docker run --rm -it --entrypoint /bin/bash tobix/pywine
```

## 02 - Cross Compile Windows

TODO: Make tiny modification in the docker build to pass arguments to compile it.

### 1.1 - Nuitka

Install `nuitka` and `mfc42.dll`dependency. 

```
$ wine python -m pip install nuitka

$ winetricks -q mfc42
```

You can now cross-compile the python (`.py`) files into windows executable files (`.exe`). Don't worry about the error message `depends.exe`. It should be compiled if you check.

```
$ wine cmd.exe /c nuitka --standalone --onefile file.py

$ wine python -m nuitka --standalone --onefile file.py

$ docker run -v $(pwd):/build tobix/pywine "wine python -m nuitka --standalone --onefile file.py"

$ file file.dist/file.exe 
file.dist/file.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
```

### 1.2 - PyInstaller

For docker it is already preinstalled so you can skip it.

```
$ wine python -m pip install pyinstaller
```

You can now cross-compile the python (`.py`) files into windows executable files (`.exe`).

```
$ wine pyinstaller -F -w file.py

$ docker run -v $(pwd):/build tobix/pywine "wine pyinstaller -F -w file.py"

$ file dist/file.exe 
dist/file.exe: PE32+ executable (GUI) x86-64, for MS Windows
```

---
## References

- [Python](https://python.org)

- [Nuitka](https://nuitka.net/)

- [Pyinstaller](https://pyinstaller.org/en/stable/)

- [webcomics: pywine](https://github.com/webcomics/pywine)

- [MakeWorld: How to create Windows EXEs for Python on Linux, using PyInstaller and WINE](https://www.makeworld.space/2021/10/linux-wine-pyinstaller.html)