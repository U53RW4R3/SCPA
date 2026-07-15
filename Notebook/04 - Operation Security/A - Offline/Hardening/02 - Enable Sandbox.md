# 02 - Enable Sandbox

## 2.1 - Basic

Load basic profiles to restrict the environment.

```
$ firejail
```

List running sandboxes.

```
$ firejail --list
```

## 2.2 - Sandbox Program

Private mode.

```
$ firejail --private <program>
```

Sandbox AppImage.

```
$ firejail --appimage program_name.AppImage

$ firejail --appimage $(which program_name.AppImage)
```

Sandbox the window server to prevent keylogging.

```
$ firejail --x11=xorg <program>
```

Drop all capabilities. To put it simply the application must have a limited set of privileges to run even as root.

```
$ firejail --caps.drop=all --noprofile bash
```

## 2.3 - Restrict Filesystem

Create a one-way secure state to prevent any aggressive attempts terminated by the kernel.

```
$ firejail --seccomp
```

Whitelist the directory path.

```
$ firejail --whitelist envince /tmp/file.pdf
```

Isolate in a temporary `/dev` directory.

```
$ firejail --private-dev
```

Create a temporary directory.

```
$ firejail --private-tmp
```

Prevent privilege escalation

```
$ firejail --nonewprivs
```

Prevent fileless payload to execute on the memory.

```
$ firejail --memory-deny-write-execute
```

## 2.4 - Restrict Network Access

```
$ firejail -net=none firefox

$ firejail -net=<interface> firefox
```

Specify DNS nameserver to launch the web browser. This prevents DNS leaks.

```
$ firejail --private --dns=1.1.1.1 firefox
```

## 2.5 - Limited Access

Restrict the commands for the user to run. 

```
$ firejail --private-bin=bash,ls,cat
```

Run a program with a specific user.

```
$ firejail --user=<username> firefox

$ firejail --user=guestuser firefox
```

## 2.6 - Network Monitoring

```
$ firejail --dnstrace
```

## 2.7 - Custom Profiles

Load profiles in the current `$HOME` directory.

```
$ cp /etc/firejail/firefox.profile ~/.config/firejail/
```

Export a custom profile.

```
$ firejail --list > myapp.profile
```

Load profile.

```
$ firejail --profile=~/.config/firejail/myapp.profile <program>
```

## 2.8 - Integrate

Integrate it in the desktop environment.

```
$ sudo firecfg
```

Remove restricted configuration.

```
$ sudo firecfg --clean
```

## 2.9 - Isolate Environment

```
$ bwrap \
  --ro-bind /usr /usr \
  --ro-bind /bin /bin \
  --ro-bind /lib /lib \
  --ro-bind /lib64 /lib64 \
  --dev /dev \
  --proc /proc \
  --unshare-net \
  bash
```

## 2.10 - Use Cases

Sandbox a PDF viewer.

```
$ firejail --seccomp --nonewprivs --private --private-dev --private-tmp --net=none --x11 --whitelist=/tmp/file.pdf evince /tmp/file.pdf
```

---
## References

### Source Repositories

- [netblue30: firejail](https://github.com/netblue30/firejail)

### Null Byte

- [Null Byte: Locking Down Linux - Using Ubuntu as Your Primary OS, Part 3 (Application Hardening & Sandboxing)](https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-3-application-hardening-sandboxing-0185710/)

### Arch Linux Wiki

- [Arch Linux Wiki: Firejail](https://wiki.archlinux.org/title/Firejail)