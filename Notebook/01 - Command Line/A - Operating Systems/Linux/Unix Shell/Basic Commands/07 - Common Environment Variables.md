---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 07 - Common Environment Variables

TODO: Fill in the rest of the environment variables

```
$LANG
$LANGUAGE

$ locale -a

$ cat /etc/locale.gen

$ cat /etc/locale.alias

$PPID

$SECONDS

$TERM
```

| Environment Variable | Output                                                                                     | Equivalent Command        | Description                                     |
| -------------------- | ------------------------------------------------------------------------------------------ | ------------------------- | ----------------------------------------------- |
| `$PWD`               | Prints the current working directory.                                                      | `pwd`                     | Variable name of the current working directory. |
| `$BASH_COMMAND`      | Returns exact command line used to start current unix-like shell prompt session.           | None                      |                                                 |
| `$HOSTNAME`          | Prints the computer name.                                                                  | `hostname` and `uname -n` | Variable name of the computer name.             |
| `$SHELL`             | Prints the current unix shell prompt.                                                      | None                      | Variable name of the current unix-like shell.   |
| `$DATE`              | Prints the current date.                                                                   | `date`                    | Variable name of the current date.              |
| `$OSTYPE`            | `linux-gnu`                                                                                | `uname -o`                | Variable name of the operating system type.     |
| `$PATH`              | `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games` | None                      | Variable name of the path environment.          |
| `$HOSTTYPE`          | Prints the architecture.                                                                   | `uname -p` and `uname -i` | Variable name of the architecture.              |
| `$MACHTYPE`          |                                                                                            | `uname -m`                |                                                 |
| `$PS1`               |                                                                                            | None                      |                                                 |
| `$PS2`               |                                                                                            | None                      |                                                 |
| `$PS4`               |                                                                                            | None                      |                                                 |
| `$USER`              | `<username>`                                                                               | `whoami` and `id -un`     |                                                 |
| `$UID`               | Prints the user ID.                                                                        | `id -u`                   | Variable name of the user ID.                   |
| `$EUID`              | Prints the effective user ID.                                                              | `id -u`                   | Variable name of the effective user ID.         |
| `$GROUPS`            | Prints the group ID.                                                                       | `id -g`                   | Variable name of the group ID.                  |
| `$HOME`              | `/home/$USER`                                                                              | None                      |                                                 |
| `$RANDOM`            |                                                                                            | None                      |                                                 |
| `$SRANDOM`           |                                                                                            | None                      |                                                 |

---
## References

### Wikipedia

- [Wikipedia: Environment Variable](https://en.wikipedia.org/wiki/Environment_variable)