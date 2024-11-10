---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - smb
  - network-mapper
  - metasploit-framework
---
# SMB

## 01 - Usage

### 1.1 - Samba Suite Utils

#### 1.1.1 - Authentication

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
$ nmap -p 445 -Pn --script "safe or smb-enum-*" <IP>
```

## 05 - Mount Share

```
$ sudo mkdir /mnt/smb

$ sudo mount -t cifs //<IP>/<share_name> /mnt/smb

$ sudo mount -t cifs -o "port=<PORT> username=<username>,password=<password>" //<IP>/<share_name> /mnt/smb
```

---
## References

- [Enum4Linux-NG](https://github.com/cddmp/enum4linux-ng)