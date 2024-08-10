# 07 - Common Environment Variables

TODO: Fill in the rest of the environment variables

```
$GROUPS
$EUID
$UID
$RANDOM
$SRANDOM

$LANG
$LANGUAGE

$PPID

$SECONDS

$TERM
```

| Environment Variable | Output                                                                           | Command Alias             | Description                                     |
| -------------------- | -------------------------------------------------------------------------------- | ------------------------- | ----------------------------------------------- |
| `$PWD`               | Prints out the current working directory.                                        | `pwd`                     | Variable name of the current working directory. |
| `$BASH_COMMAND`      | Returns exact command line used to start current unix-like shell prompt session. | None                      |                                                 |
| `$HOSTNAME`          | `<hostname>`                                                                     | `hostname` and `uname -n` | Variable name of the computer name.             |
| `$SHELL`             | `/bin/bash`                                                                      | None                      | Variable name of the current unix-like shell.   |
| `$DATE`              | Prints out the current date.                                                     | `date`                    |                                                 |
| `$OSTYPE`            |                                                                                  | `uname -o`                |                                                 |
| `$PATH`              |                                                                                  | None                      |                                                 |
| `$HOSTTYPE`          | Prints out the architecture.                                                     | `uname -p` and `uname -i` |                                                 |
| `$MACHTYPE`          |                                                                                  | `uname -m`                |                                                 |
| `$PS1`               |                                                                                  | None                      |                                                 |
| `$PS2`               |                                                                                  |                           |                                                 |
| `$PS4`               |                                                                                  |                           |                                                 |
| `$USER`              | `<username>`                                                                     | `whoami`                  |                                                 |
| `$HOME`              | `/home/$USER`                                                                    | None                      |                                                 |
