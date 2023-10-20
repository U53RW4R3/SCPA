# Usage

## Help Menu

```
Meta shell commands
===================

    Command     Description
    -------     -----------
    help        Help menu
    background  Backgrounds the current shell session
    sessions    Quickly switch to another session
    resource    Run a meta commands script stored in a local file
    shell       Spawn an interactive shell (*NIX Only)
    download    Download files (*NIX Only)
    upload      Upload files (*NIX Only)
    source      Run a shell script on remote machine (*NIX Only)
    irb         Open an interactive Ruby shell on the current session
    pry         Open the Pry debugger on the current session
```

## Interactive Meta Shell

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