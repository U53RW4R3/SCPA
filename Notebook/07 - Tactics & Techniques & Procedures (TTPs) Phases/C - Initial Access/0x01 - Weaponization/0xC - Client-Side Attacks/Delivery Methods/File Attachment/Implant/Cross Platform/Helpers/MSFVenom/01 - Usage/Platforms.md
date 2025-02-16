# Platforms

To List all Platforms

```
$ msfvenom -l platforms

Framework Platforms [--platform <value>]
========================================

    Name
    ----
    aix
    android
    apple_ios
    arista
    brocade
    bsd
    bsdi
    cisco
    firefox
    freebsd
    hardware
    hpux
    irix
    java
    javascript
    juniper
    linux
    mainframe
    mikrotik
    multi
    netbsd
    netware
    nodejs
    openbsd
    osx
    php
    python
    r
    ruby
    solaris
    unifi
    unix
    unknown
    windows
```

```
$ cat payload.bin | msfvenom -p - -a x64 --platform windows -f exe -o shell-x64.exe
```