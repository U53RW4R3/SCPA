# MSRPC

## 01 - Manual

Authenticating with NetBIOS protocol

```
$ rpcclient -U <username>%<password> <IP>
```

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

#### 1.1.5 - LSA Query

- Enumerate SID From LSA

```
rpcclient $> lsaquery

rpcclient $> dsroledominfo
```

- SAM Lookup

```
rpcclient $> samlookupnames domain <username>

rpcclient $> samlookuprids domain <rid>
```

- Enumerating LSA Group Privileges

```
rpcclient $> lsaenumsid

rpcclient $> lookupsids <SID>

rpcclient $> lookupsids S-1-1-0

rpcclient $> lsaenumacctrights <SID>

rpcclient $> lsaenumacctrights S-1-1-0

rpcclient $> lsalookupprivvalue SeCreateTokenPrivilege
```

LSA Query Security Objects

```
rpcclient $> lsaquerysecobj
```

## 02 - Network Mapper

```
$ nmap -p 135,445,593 -Pn --script msrpc-enum <IP>
```

---
## References

- [0xffsec: MSRPC (Microsoft Remote Procedure Call)](https://0xffsec.com/handbook/services/msrpc/)

- [Hacktricks: 135 Pentesting MSPRC](https://book.hacktricks.xyz/pentesting/135-pentesting-msrpc)