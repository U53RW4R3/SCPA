# Python

## 01 - Nuitka

### 1.1 - Linux

`$ nuitka --onefile shell.py`

### 1.2 - Wine

#### 1.2.1 - Setup specific version via winetricks

- Choose **Select the default wineprefix**.

![[01 - Choose a WinePrefix.png]]

- **Run winecfg**

![[02 - WineCFG.png]]

- Choose specific windows version.

![[03 - Select Windows 10 Version.png]]

TODO: Fill this info

- Then you go ahead to the python download link (https://www.python.org/downloads/windows/) and choose the latest version. Execute with the wine installer and follow the wizard instructions. Once you're done download and install PyPI (Python Package Manager).

Note: it's not working withe the current version.

```
$ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && \
wine python.exe get-pip.py
```

- Install Nuitka

```
$ https://nuitka.net/releases/Nuitka-1.6.6.zip && \
7z x Nuitka-1.6.6.zip && cd Nuitka-1.6.6 && \
wine python.exe setup.py install
```

## 02 - PyInstaller

### 2.1 - Wine

```
$ git clone https://github.com/pyinstaller/pyinstaller && \
cd pyinstaller/ && wine python.exe setup.py install
```

---
## References

- [Python](https://python.org)

- [Python Get-PIP](https://github.com/pypa/get-pip)

- [Docker Pyinstaller](https://github.com/cdrx/docker-pyinstaller)

- [Nuitka](https://nuitka.net/)