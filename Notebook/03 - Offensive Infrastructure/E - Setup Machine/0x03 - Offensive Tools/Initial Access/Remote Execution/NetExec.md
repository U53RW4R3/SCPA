---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - offensive-tools
  - initial-access
  - netexec
---
# NetExec

## 01 - Installation

Install the dependencies according to your package manager.

```
$ sudo apt install -y pipx git python3-aardwolf python3-aesedb python3-aiocmd python3-aioconsole python3-aiosmb python3-aiosqlite python3-aiowinreg python3-all-dev python3-anyjson python3-arc4 python3-argcomplete python3-asciitree python3-asn1tools python3-asyauth python3-asysocks python3-backcall python3-bs4 python3-beniget python3-bitstruct bloodhound.py python3-dateutil python3-diskcache python3-dploot python3-dsinternals python3-gast python3-libnmap python-lsassy python3-masky python3-minidump python3-minikerberos python3-msgpack python3-msldap python3-neo4j python3-neobolt python3-neotime python3-oscrypto python3-paramiko python3-pickleshare python3-poetry-dynamic-versioning python3-pyasn1-modules python3-pyatspi python3-pylnk3 python3-pypsrp python3-pypykatz python3-pythran python3-pywerview python3-requests python3-requests-toolbelt python3-rich python3-spnego python3-sqlalchemy python3-termcolor python3-terminaltables python3-xmltodict
```

## 02 - Install NetExec

```
$ pipx ensurepath && \
pipx install git+https://github.com/Pennyw0rth/NetExec
```

## 02 - Post Installation

Setup auto tab complete for `/bin/bash` shell prompt.

```
$ register-python-argcomplete nxc >> ~/.bashrc
```

For `/bin/zsh` shell prompt.

```
$ register-python-argcomplete nxc >> ~/.zshrc
```