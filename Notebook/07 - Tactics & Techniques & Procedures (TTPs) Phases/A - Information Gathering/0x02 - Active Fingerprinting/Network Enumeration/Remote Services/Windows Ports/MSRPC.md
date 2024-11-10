---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - msrpc
  - network-mapper
---
# MSRPC

> [!INFO]
> **Windows Management Instrument (WMI)** is also part of **Remote Procedure Call (RPC)**.

## 01 - Manual

Authenticating with **MSRPC** protocol

```
$ rpcclient -U <username>%<password> <IP>
```

## 02 - Network Mapper

```
$ nmap -p 135 -Pn -n <IP>
```

---
## References

- [0xffsec: MSRPC (Microsoft Remote Procedure Call)](https://0xffsec.com/handbook/services/msrpc/)

- [Hacktricks: 135 Pentesting MSPRC](https://book.hacktricks.xyz/pentesting/135-pentesting-msrpc)