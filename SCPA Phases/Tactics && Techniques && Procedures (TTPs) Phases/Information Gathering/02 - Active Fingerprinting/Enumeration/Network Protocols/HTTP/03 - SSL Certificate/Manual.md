# Manual

## 01 - Certificate dates

`$ echo | openssl s_client -connect <URL>:443 2>/dev/null | openssl x509 -dates -noout`

## 02 - Gather Subdomains

```
$ true | openssl s_client -connect <IP>:443 2>/dev/null | openssl x509 -noout -text | perl -l -0777 -ne '@names=/\bDNS:([^\s,]+)/g; print join("\n", sort @names);'
```

---
## References

- [0xffsec Handbook: Subdomain Enumeration](https://0xffsec.com/handbook/information-gathering/subdomain-enumeration/)