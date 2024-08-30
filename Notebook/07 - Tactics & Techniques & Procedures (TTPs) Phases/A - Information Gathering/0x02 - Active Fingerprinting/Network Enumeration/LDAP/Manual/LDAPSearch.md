# LDAPSearch

## 01 - Usage

> [!INFO] What TLD looks like?
> TLD (Top Level Domain) looks like this `.com`, `.net`, etc.

```
$ ldapsearch -x ldap://<IP> -D '<DOMAIN>\<username>' -w '<password>' -b "DC=<1_subdomain>,DC=<tdl>"
```

---
## References

- [Hacktricks: Pentesting LDAP](https://book.hacktricks.xyz/pentesting/pentesting-ldap)