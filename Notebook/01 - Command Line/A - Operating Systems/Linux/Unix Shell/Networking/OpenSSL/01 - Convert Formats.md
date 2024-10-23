---
author(s):
  - Userware
tags:
  - command-line
  - cryptography
  - linux
---
# 01 - Convert Formats

Convert from `.pem` to `.der`.

```
openssl x509 -outform der -in cert.pem -out cert.der
```

Convert from `.der` to `.pem`.

```
$ openssl x509 -inform der -in cert.cer -out cert.pem
```

Convert from `.pkcs` to `.pem`.

```
openssl pkcs12 -in key.pfx -out key.pem -nodes
```

Convert from `.pem` to `.pkcs`.

```
$ openssl pkcs12 -export -out cert.pfx -inkey priv.key -in cert.crt -certfile ca.crt
```