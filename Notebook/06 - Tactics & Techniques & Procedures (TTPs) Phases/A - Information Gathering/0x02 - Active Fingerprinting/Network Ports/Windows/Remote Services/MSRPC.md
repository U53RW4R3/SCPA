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

### 3.1 - Protocol Name

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

### 3.2 - Status Code

| Status Code                                              | Description                                                        |
| -------------------------------------------------------- | ------------------------------------------------------------------ |
| Authentication only, exit status `0` or `ERROR_SUCCESS`. | Successful authentication.                                         |
| `ERROR_INVALID_PARAMETER`                                | An invalid parameter was passed to the RPC call.                   |
| `ERROR_ACCESS_DENIED`                                    | Access to the requested resource is denied.                        |
| `ERROR_NO_SUCH_FILE`                                     | The specified file does not exist.                                 |
| `ERROR_NO_SUCH_SERVICE`                                  | The specified service does not exist.                              |
| `ERROR_SERVER_UNAVAILABLE`                               | The RPC server is unavailable.                                     |
| `ERROR_CALL_NOT_IMPLEMENTED`                             | The requested operation is not implemented.                        |
| `ERROR_CONNECTION_REFUSED`                               | The connection to the RPC server was refused.                      |
| `ERROR_TIMEOUT`                                          | The operation timed out.                                           |
| `ERROR_NETWORK_UNREACHABLE`                              | The network is unreachable.                                        |
| `ERROR_CONNECTION_RESET`                                 | The connection was reset by the peer.                              |
| `ERROR_NOT_ENOUGH_MEMORY`                                | Insufficient memory to complete the operation.                     |
| `ERROR_INTERNAL_ERROR`                                   | An internal error occurred in the RPC server.                      |
| `ERROR_INVALID_USER_BUFFER`                              | The supplied user buffer is not valid for the requested operation. |
| `RPC_S_SERVER_UNAVAILABLE`                               | The RPC server is unavailable.                                     |
| `RPC_S_INVALID_STRING_BINDING`                           | The string binding is invalid.                                     |
| `RPC_S_PROTOCOL_ERROR`                                   | A protocol error occurred in the RPC call.                         |
| `RPC_S_INTERNAL_ERROR`                                   | An internal error occurred in the RPC server.                      |
| `RPC_S_UUID_LOCAL_ONLY`                                  | A UUID that is valid only on this computer has been allocated.     |
| `RPC_S_PROXY_ACCESS_DENIED`                              | Access to the proxy is denied.                                     |
| `RPC_S_CALL_IN_PROGRESS`                                 | A remote procedure call is already in progress for this thread.    |

---
## References

### Hacktricks

- [Hacktricks: Pentesting MSPRC](https://book.hacktricks.wiki/en/network-services-pentesting/135-pentesting-msrpc.html)

### Hacking Articles

- [Hacking Articles: Active Directory Enumeration RPCClient](https://www.hackingarticles.in/active-directory-enumeration-rpcclient/)

### 0xffsec

- [0xffsec: MSRPC (Microsoft Remote Procedure Call)](https://0xffsec.com/handbook/services/msrpc/)