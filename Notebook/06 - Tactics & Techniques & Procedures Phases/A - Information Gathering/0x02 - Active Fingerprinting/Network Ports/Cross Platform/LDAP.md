---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-protocols
  - ldap
  - network-mapper
---
# LDAP

## 01 - Banner Grab

```
$ nmap -p 389,636,3268,3269 -Pn -sV <IP>
```

## 02 - Authentication

### 2.1 - LDAPDomainDump

```
$ ldapdomaindump <IP> [-r <domain_controller_IP>] -u '<domain>\<username>' -p '<password>' [--authtype SIMPLE] --no-json --no-grep -o ldap-loot
```

### 2.2 - LDAPSearch

> [!INFO] What TLD looks like?
> TLD (Top Level Domain) looks like this `.com`, `.net`, etc.

```
$ ldapsearch -x -D '<DOMAIN>\<username>' -w '<password>' -b "[DC=<subdomain>,]DC=<domain>,DC=<tdl>" -H ldap://<domain_controller_IP>
```

---
## References

### Hacktricks

- [Hacktricks: Pentesting LDAP](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-ldap.html)