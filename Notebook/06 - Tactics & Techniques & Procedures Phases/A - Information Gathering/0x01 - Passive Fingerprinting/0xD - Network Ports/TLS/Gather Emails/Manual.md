# Manual

```
$ echo -n | openssl s_client -connect microsoft.com:443 -showcerts </dev/null 2>/dev/null | openssl x509 -noout -email
```