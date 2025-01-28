# Installation

Search Tag(s): #cobalt-strike #command-and-control

## 01 - Dependencies

Install the required dependencies according to your package manager.

```
$ sudo apt install -y mingw-w64 nasm default-jdk default-jre

$ sudo pacman -S mingw-w64-binutils mingw-w64-crt mingw-w64-gcc mingw-w64-headers mingw-w64-winpthreads nasm jdk-openjdk jre-openjdk
```

## 02 - Launch teamserver and operator client

```
$ sudo ./teamserver <IP> <password> /path/to/malleable_c2.profile

$ ./cobaltstrike.sh
```