# Manual

## 01 - OpenSSL

`$ echo | openssl s_client -connect <URL>:443 2>/dev/null | openssl x509 -dates -noout`