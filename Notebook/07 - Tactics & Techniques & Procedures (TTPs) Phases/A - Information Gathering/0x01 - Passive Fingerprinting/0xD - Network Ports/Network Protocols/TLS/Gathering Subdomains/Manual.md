# Manual

## 01 - Setup TLS

TODO: manually configure a wide compatibility for legacy OpenSSL to interact weak encryption

`$ cat /etc/ssl/kali.cnf`

---

```
```

`$ cat /etc/ssl/openssl.cnf`

---

```
[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
MinProtocol = TLS1.2
CipherString = DEFAULT@SECLEVEL=2
```

## 01 - Certificate Dates

```
$ echo | openssl s_client -connect <URL>:443 2>/dev/null | openssl x509 -dates -noout
```

## 02 - Gather Subdomains

```
$ echo -n | openssl s_client -connect <IP>:443 2>/dev/null | openssl x509 -noout -text | grep -oP '\bDNS:[^\s,]+' | sed 's/^DNS://' | sort -u

$ true | openssl s_client -connect <IP>:443 2>/dev/null | openssl x509 -noout -text | grep -oP '\bDNS:[^\s,]+' | sed 's/^DNS://' | sort -u

$ echo -n | openssl s_client -connect <IP>:443 2>/dev/null | openssl x509 -noout -text | perl -l -0777 -ne '@names=/\bDNS:([^\s,]+)/g; print join("\n", sort @names);'

$ true | openssl s_client -connect <IP>:443 2>/dev/null | openssl x509 -noout -text | perl -l -0777 -ne '@names=/\bDNS:([^\s,]+)/g; print join("\n", sort @names);'
```

---
## References

### Kali Documentation

- [Kali Docs: OpenSSL Configuration](https://www.kali.org/docs/general-use/openssl-configuration/)

### One Oasis

- [One Oasis: Testing Legacy Systems with Kali Linux](https://medium.com/@oneoasis/testing-legacy-systems-with-latest-kali-linux-50b884bd3ece)

### 0xffsec

- [0xffsec Handbook: Subdomain Enumeration](https://0xffsec.com/handbook/information-gathering/subdomain-enumeration/)