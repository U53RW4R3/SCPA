---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - ldap
  - network-mapper
---
# LDAP

## 01 - Usage

### 1.1 - LDAPDomainDump

```
$ ldapdomaindump <IP> [-r <domain_controller_IP>] -u '<domain>\<username>' -p '<password>' [--authtype SIMPLE] --no-json --no-grep -o ldap-loot
```

### 1.2 - LDAPSearch

> [!INFO] What TLD looks like?
> TLD (Top Level Domain) looks like this `.com`, `.net`, etc.

```
$ ldapsearch -x -D '<DOMAIN>\<username>' -w '<password>' -b "[DC=<subdomain>,]DC=<domain>,DC=<tdl>" -H ldap://<domain_controller_IP>
```

---
## References

### Hacktricks

- [Hacktricks: Pentesting LDAP](https://book.hacktricks.xyz/pentesting/pentesting-ldap)

### Rapid7

- [Rapid7: Metasploit Framework - LDAP Auxiliary Module](https://docs.metasploit.com/docs/pentesting/metasploit-guide-ldap.html)