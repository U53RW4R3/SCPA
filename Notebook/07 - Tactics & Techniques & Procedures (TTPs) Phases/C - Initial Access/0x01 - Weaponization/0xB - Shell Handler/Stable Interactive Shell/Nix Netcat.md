# Nix Netcat

## 01 - Spawn TTY Shell

### 1.1 - Cross Platform

Using the GNU readline wrapper with arrow keys. You can use this when using a normal reverse shell for penetrating Windows machine.

```
userware@hackware-os:~$ rlwrap nc <target_IP> <target_PORT>
```

The `-f .` flag will make rlwrap use the current history file as a completion word list, and `-r` put all words seen on input and output on the completion list.

```
userware@hackware-os:~$ rlwrap -r -f . nc <target_IP> <target_PORT>
```

### 1.2 - Linux

#### 1.1.1 - Python

```
$ python -c 'import pty; pty.spawn("/bin/bash")'
CTRL+Z

userware@hackware-os:~$ echo $TERM && tput lines && tput cols
```

In attacker machine for `/bin/bash`.

```
userware@hackware-os:~$ stty raw -echo
fg
```

In attacker machine for `/bin/zsh`.

```
userware@hackware-os:~$ stty raw -echo; fg
reset
export SHELL=/bin/bash
```

Display the terminal colors (You can skip this step if the shell is stabilized).

```
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```

#### 1.1.2 - Script

This is a universal method for GNU/Linux and Unix-like operating systems.

```
$ script -qc /bin/bash /dev/null
CTRL+Z

userware@hackware-os:~$ echo $TERM && tput lines && tput cols
```

In attacker machine for `/bin/bash`.

```
userware@hackware-os:~$ stty raw -echo
userware@hackware-os:~$ fg
```

In attacker machine for `/bin/zsh`.

```
userware@hackware-os:~$ stty raw -echo; fg

$ reset
$ export SHELL=/bin/bash
```

Display the terminal colors (You can skip this step if the shell is stablized).

```
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```

#### 1.1.3 - Expect

Using `expect` to get a TTY

```
#!/usr/bin/expect
# Spawn a shell, then allow the user to interact with it.
# The new shell will have a good enough TTY to run tools like ssh, su and login
spawn sh
interact
```

Output

```
$ nc -lnvp 1234
listening on [any] 1234 ...
connect to [127.0.0.1] from (UNKNOWN) [127.0.0.1] 48257
sh: no job control in this shell
sh-3.2$ su -
su: must be run from a terminal
sh-3.2$ expect sh.exp
spawn sh
sh-3.2$ su -
Password:  mypassword
localhost ~ #
```

### 1.3 - BSD

#### 1.3.1 - Script

```
$ exec script -q /dev/null /bin/bash
```

### 1.4 - Windows

Note: Refer to fully interactive [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Desktop/Windows/Payloads/One-Liners/Reverse Shells/PowerShell#^d57486|powershell]].

#### 1.3.1 - Method One

This will set the terminal size automatically without passing the `rows` and `cols` manually.

```
userware@hackware-os:~$ stty raw -echo; (stty size; cat) | nc -lvnp <PORT>
```

#### 1.3.2 - Method Two

When you encounter an problem to ensure that the `cols` and `rows` are set manually.

```
userware@hackware-os:~$ stty size

userware@hackware-os:~$ nc -lvnp <PORT>

PS C:\> CTRL+Z
```

In attacker machine for `/bin/bash`.

```
userware@hackware-os:~$ stty raw -echo
userware@hackware-os:~$ fg
```

In attacker machine for `/bin/zsh`.

```
userware@hackware-os:~$ stty raw -echo; fg
```

#### 1.3.3 - Method Three - Upgrade

You can also upgrade your current shell to a fully interactive shell. In this case it's important that you set `rows` and `cols` size when calling the `Invoke-ConPtyShell` function.

```
userware@hackware-os:~$ stty size

userware@hackware-os:~$ nc -lvnp <PORT>

PS C:\> CTRL+Z
```

In attacker machine for `/bin/bash`.

```
userware@hackware-os:~$ stty raw -echo
userware@hackware-os:~$ fg
```

In attacker machine for `/bin/zsh`.

```
userware@hackware-os:~$ stty raw -echo; fg
```

---
## References

### Source Repository

- [hackerschoice: THC's favourite Tips, Tricks & Hacks (Cheat Sheet)](https://github.com/hackerschoice/thc-tips-tricks-hacks-cheat-sheet)

- [antonioCoco: ConPtyShell](https://github.com/antonioCoco/ConPtyShell)

### Hacktricks

- [Hacktricks: Shells Full TTYs](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/full-ttys.html)

### ROPNOP

- [ROPNOP: Upgrading Simple Shells to Fully Interactive TTYs](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/)

### Pentest Monkey

- [Pentest Monkey: Post Exploitation Without a TTY](https://pentestmonkey.net/blog/post-exploitation-without-a-tty)

### Enlace Hacktivista

- [Enlace Hacktivista: Stabilizing reverse shells](https://enlacehacktivista.org/index.php?title=Stabilizing_reverse_shells)

### Ivan IT Learning

- [Ivan IT Learning: Interactive shells for Windows](https://ivanitlearning.wordpress.com/2021/04/27/interactive-shells-for-windows/)