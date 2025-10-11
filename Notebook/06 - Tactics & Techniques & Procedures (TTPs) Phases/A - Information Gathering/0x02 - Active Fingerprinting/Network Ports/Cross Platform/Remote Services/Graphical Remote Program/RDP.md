# RDP

## 01 - Banner Grab

### 1.1 - Nmap

```
$ nmap -p 3389 -Pn -sV <IP>
```

### 1.2 - Metasploit

```
msf > use auxiliary/scanner/rdp/rdp_scanner

msf auxiliary(scanner/rdp/rdp_scanner) > options

Module options (auxiliary/scanner/rdp/rdp_scanner):

   Name             Current Setting  Required  Description
   ----             ---------------  --------  -----------
   DETECT_NLA       true             yes       Detect Network Level Authentication (NLA)
   RDP_CLIENT_IP    192.168.0.100    yes       The client IPv4 address to report during connect
   RDP_CLIENT_NAME  rdesktop         no        The client computer name to report during connect, UNSET = random
   RDP_DOMAIN                        no        The client domain name to report during connect
   RDP_USER                          no        The username to report during connect, UNSET = random
   RHOSTS                            yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT            3389             yes       The target port (TCP)
   THREADS          1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/rdp/rdp_scanner) > set rhosts <target_IP>

msf auxiliary(scanner/rdp/rdp_scanner) > set threads 4

msf auxiliary(scanner/rdp/rdp_scanner) > set rdp_client_IP <client_IP>

msf auxiliary(scanner/rdp/rdp_scanner) > set rdp_client_name <client_name>

msf auxiliary(scanner/rdp/rdp_scanner) > run -j
```

## 02 - RDP Encryption Algorithm

```
$ nmap -p 3389 -Pn -sV --script rdp-enum-encryption <IP>
```

## 03 - NTLM Information

```
$ nmap -p 3389 -Pn -sV --script rdp-ntlm-info <IP>
```

## 04 - Status Code Table Reference

| Status Code                                                                                                                                                                              | Description                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Authentication only, exit status `0`.                                                                                                                                                    | Successful authentication with RDP permissions.                           |
| `ERRCONNECT_AUTHENTICATION_FAILED [0x00020006]`<br>`ERRCONNECT_AUTHENTICATION_FAILED [0x00020009]`<br>`ERRCONNECT_LOGON_FAILURE [0x00020009]`<br>`ERRCONNECT_LOGON_FAILURE [0x00020014]` | Authentication failure due to invalid credentials.                        |
| `ERRCONNECT_SECURITY_NEGO_FAILED [0x0002000C]`                                                                                                                                           | Security negotiation failed, often due to incompatible security settings. |
| `ERRCONNECT_PASSWORD_EXPIRED [0x0002000E]`<br>`ERRCONNECT_PASSWORD_CERTAINLY_EXPIRED [0x0002000F]`<br>`ERRCONNECT_PASSWORD_MUST_CHANGE [0x00020013]`                                     | Password expired.                                                         |
| `ERRCONNECT_ACCOUNT_LOCKED_OUT`                                                                                                                                                          | User account locked out.                                                  |
| `ERRCONNECT_ACCOUNT_DISABLED [0x00020012]`                                                                                                                                               | User account disabled.                                                    |
| `ERRCONNECT_ACCOUNT_EXPIRED [0x00020019]`                                                                                                                                                | User account expired.                                                     |
| `ERRCONNECT_DNS_NAME_NOT_FOUND`                                                                                                                                                          | DNS nameserver absent.                                                    |
| `ERRINFO_SERVER_INSUFFICIENT_PRIVILEGES [0x00000009]`                                                                                                                                    | Successful authentication yet lacks RDP permissions.                      |
| `ERRCONNECT_CONNECT_TRANSPORT_FAILED [0x0002000D]`                                                                                                                                       | Successful authentication yet connect transport layer failed.             |

---
## References

### Hacktricks

- [Hacktricks: Pentesting RDP](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-rdp.html)