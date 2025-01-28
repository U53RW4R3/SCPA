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

## 03 - Table Reference

| Protocol Name | Name                                   | Description                                                         |
|---------------|----------------------------------------|---------------------------------------------------------------------|
| MS-BKRP       | BackupKey                             | Protocol for securely backing up cryptographic keys.               |
| MS-DCOM       | Distributed Component Object Model    | Protocol for communication between software components.            |
| MS-DMRP       | Disk Management                       | Protocol for managing disk partitions and volumes.                 |
| MS-DRSR       | Directory Replication Service         | Protocol for Active Directory replication between domain controllers. |
| MS-DSSP       | Directory Services Setup              | Protocol for setting up directory services.                        |
| MS-FAX        | Fax Server and Client                 | Protocol for managing fax services on Windows.                     |
| MS-ICPR       | ICertPassage                          | Protocol for certificate handling and passage.                     |
| MS-IMSA       | IMSAdminBaseW                         | Protocol for Internet Information Services (IIS) management.       |
| MS-IRP        | Inetinfo                              | Protocol for IIS (Internet Information Services) core operations.  |
| MS-LSAD       | Local Security Authority (Domain Policy) | Protocol for managing domain policies via Local Security Authority. |
| MS-LSAT       | Local Security Authority (Translation Methods) | Protocol for translating security identifiers (SIDs) to names.    |
| MS-MSRP       | Messenger Service                     | Protocol for managing the Messenger Service.                       |
| MS-NRPC       | Netlogon                              | Protocol for secure channel establishment and authentication.      |
| MS-PAR        | Print System Asynchronous             | Protocol for asynchronous print operations.                        |
| MS-RPRN       | Print System                          | Protocol for printer management.                                   |
| MS-RSMP       | Removable Storage Manager             | Protocol for managing removable storage devices.                   |
| MS-SAMR       | Security Account Manager (Client-to-Server) | Protocol for client-to-server account management.               |
| MS-SAMS       | Security Account Manager (Server-to-Server) | Protocol for server-to-server account synchronization.           |
| MS-SCMR       | Service Control Manager               | Protocol for managing Windows services.                            |
| MS-SRVS       | Server Service                        | Protocol for file and printer sharing services.                    |
| MS-TRP        | Telephony                             | Protocol for managing telephony services.                          |
| MS-W32T       | W32Time                               | Protocol for Windows Time Service synchronization.                 |
| MS-WKST       | Workstation Service                   | Protocol for workstation services on Windows.                      |
| MS-WMI        | Windows Management Instrumentation    | Protocol for managing and monitoring Windows systems.              |
| MS-DMR        | Disk Management                       | Protocol for managing disk partitions and volumes.                 |

---
## References

### Hacktricks

- [Hacktricks: 135 Pentesting MSPRC](https://book.hacktricks.xyz/pentesting/135-pentesting-msrpc)

### 0xffsec

- [0xffsec: MSRPC (Microsoft Remote Procedure Call)](https://0xffsec.com/handbook/services/msrpc/)