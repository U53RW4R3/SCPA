---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-ports
  - smb
  - network-mapper
  - metasploit-framework
---
# SMB

## 01 - Usage

### 1.1 - Samba Suite Utils

```
$ smbclient -U "<username>%<password>" -L //<IP>

$ smbclient -U "<username>" --password="<password>" -L //<IP>
```

Pass The Hash

```
$ smbclient -U "<username>" --pw-nt-hash <nt_hash> -L //<IP>
```

Set protocol.

```
$ smbclient -m smb<1|2|3> -U "" //<IP>/<share>

$ smbclient --option="client min protocol=core" -U "" //<IP>/<share>
```

### 1.2 - Impacket

```
$ smbclient.py [<domain>/]<username>:<password>@<IP>

$ smbclient.py [<domain>/]<username>@<IP> -hashes :<nt_hash>
```

### 1.3 - SMBMap

Authentication syntax

```
$ smbmap -u "<username>" -p "< <password> | <nt_hash> >" -H <IP> [-P <PORT>]
```

### 1.4 - Enum4Linux-NG

```
$ enum4linux-ng -A -u "<username>" -p "<password>" <IP>
```

Pass the Hash

```
$ enum4linux-ng -A -u "<username>" -H <nt_hash> <IP>
```

Pass the Ticket

```
$ export KRB5CCNAME=/path/to/file.ccache

$ enum4linux-ng -A -u "<username>" -K <IP>
```

### 1.5 - NetExec

Authentication syntax

```
$ netexec smb <IP> -u "<username>" -p "<password>" [-d <domain> | --local-auth]

$ netexec smb <IP> -u "<username>" -H "<nt_hash>" [-d <domain> | --local-auth]
```

## 02 - Banner Grab

### 2.1 - Table Reference

| SMB Version | Windows Operating System Versions                 |
| ----------- | ------------------------------------------------- |
| SMB1        | Windows 2000<br>Windows XP<br>Windows Server 2003 |
| SMB2        | Windows Vista SP1<br>Windows Server 2008          |
| SMB2.1      | Windows 7<br>Windows Server 2008 R2               |
| SMB3        | Windows 8<br>Windows Server 2012                  |

### 2.2 - Network Mapper

```
$ nmap -p 445 -Pn -n --script "safe or smb-enum-*" <IP>
```

### 2.3 - Metasploit

```
msf > use auxiliary/scanner/smb/smb_version

msf auxiliary(scanner/smb/smb_version) > options

Module options (auxiliary/scanner/smb/smb_version):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   THREADS  1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smb/smb_version) > set rhosts <IP>

msf auxiliary(scanner/smb/smb_version) > set threads 5

msf auxiliary(scanner/smb/smb_version) > run -j
```

## 03 - System Volume Information

```
$ smbclient -U "[<domain>/]<username>%<password>" //<IP>/SYSVOL

$ smbclient -U "[<domain>/]<username>" --pw-nt-hash <nt_hash> //<IP>/SYSVOL

smb: \> ls
```

## 04 - Network Enumeration

```
$ nmap -p 445 -Pn -n --script "safe or smb-enum-*" <IP>
```

## 05 - Mount Share

```
$ sudo mkdir /mnt/smb

$ sudo mount -t cifs //<IP>/<share_name> /mnt/smb

$ sudo mount -t cifs -o "[port=<PORT>] username=<username>,password=<password>,rw" //<IP>/<share_name> /mnt/smb
```

When authenticating a samba unix server.

```
$ sudo mount -t cifs -o "[port=<PORT>] vers=1.0,user=root,uid=0,gid" //<IP>/<share_name> /mnt/smb
```

## 06 - RPC Endpoints

```
$ nmap -p 445 -Pn -n --script msrpc-enum <IP>
```

^4eb6e0

## 07 - Code Table Reference

| Status Code                                       | Description                                                                                 |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Authentication only, exit status `0`.             | Successful authentication.                                                                  |
| `ERRNO_LOGON_FAILURE`                             | Authentication failure due to invalid credentials.                                          |
| `ERRNO_NOT_ENOUGH_MEMORY`                         | Insufficient memory to complete the operation.                                              |
| `ERRNO_CONNECTION_REFUSED`                        | The connection to the SMB server was refused.                                               |
| `ERRNO_INVALID_PARAMETER`                         | An invalid parameter was passed to the SMB command.                                         |
| `ERRNO_NO_SUCH_FILE`<br>`ERRNO_NO_SUCH_DIRECTORY` | The specified file or directory does not exist.                                             |
| `ERRNO_ACCESS_DENIED`                             | Access to the file or directory is denied.                                                  |
| `ERRNO_FILE_CONTAINS_MALWARE`                     | The operation was blocked because the file contains malware or potentially harmful content. |
| `ERRNO_PASSWORD_EXPIRED`                          | Password expired.                                                                           |
| `ERRNO_ACCOUNT_LOCKED_OUT`                        | User account locked out.                                                                    |
| `ERRNO_ACCOUNT_DISABLED`                          | User account disabled.                                                                      |
| `ERRNO_SESSION_KEY_EXPIRED`                       | The session key has expired.                                                                |
| `ERRNO_NETWORK_UNREACHABLE`                       | The network is unreachable.                                                                 |
| `ERRNO_CONNECTION_RESET`                          | The connection was reset by the peer.                                                       |
| `ERRNO_UNSUPPORTED_FEATURE`                       | The requested feature is not supported by the server.                                       |
| `ERRNO_SERVER_ERROR`                              | An unspecified server error occurred.                                                       |


---
## References

### Source Repositories

- [Enum4Linux-NG](https://github.com/cddmp/enum4linux-ng)

### Hacktricks

- [Hacktricks: Pentesting SMB](https://book.hacktricks.wiki/en/pentesting/pentesting-smb.html)

### Hacking Articles

- [Hacking Articles: A Little Guide to SMB Enumeration](https://www.hackingarticles.in/a-little-guide-to-smb-enumeration/)

### 0xffsec

- [0xffsec: SMB Protocol Negotiation Failed](https://0xffsec.com/handbook/notes/smb-protocol-negotiation-failed/)

### Kali Documentation

- [Kali Docs: Kali Samba Configuration](https://www.kali.org/docs/general-use/samba-configuration/)