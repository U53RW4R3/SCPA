# Setup

## 01 - Windows

Install the [Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools). Turn off aliases for Python

Search **Manage app execution aliases.**

![[01 - Windows Search Bar.png]]

Turn off the **App Installers**

![[02 - Manage app execution aliases.png]]

Then install the Python packages.

```
C:\> git clone https://github.com/mgeeky/PackMyPayload.git
cd PackMyPayload
python -m pip install -r requirements.txt
```

## 02 - Linux

Install the dependencies.

```
$ sudo apt install -y python3-py7zr python3-pycdlib python3-colorama python3-pypdf2

$ pip3 install zipfile2 pyminizip cabarchive
```

Clone the repository

```
$ sudo git clone https://github.com/mgeeky/PackMyPayload.git /opt/exploitation/PackMyPayload && \
sudo ln -sf /opt/exploitation/PackMyPayload/PackMyPayload.py /usr/local/bin/packmypayload && \
sudo chmod 755 /usr/local/bin/packmypayload
```

---
## References

### Source Repositories

- [PackMyPayload](https://github.com/mgeeky/PackMyPayload)

### Microsoft

- [Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)