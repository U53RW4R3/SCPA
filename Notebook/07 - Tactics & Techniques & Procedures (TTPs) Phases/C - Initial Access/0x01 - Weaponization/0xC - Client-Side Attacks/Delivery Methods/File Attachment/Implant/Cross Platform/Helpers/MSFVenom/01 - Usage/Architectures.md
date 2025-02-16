# Architectures

To list all the architectures.

```
$ msfvenom -l archs

Framework Architectures [--arch <value>]
========================================

    Name
    ----
    aarch64
    armbe
    armle
    cbea
    cbea64
    cmd
    dalvik
    firefox
    java
    mips
    mips64
    mips64le
    mipsbe
    mipsle
    nodejs
    php
    ppc
    ppc64
    ppc64le
    ppce500v2
    python
    r
    ruby
    sparc
    sparc64
    tty
    x64
    x86
    x86_64
    zarch
```

```
$ msfvenom -a x64 -p windows/x64/exec cmd=notepad.exe -f exe -o shell-x64.exe
```