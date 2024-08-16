# Manual

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

### 1.5 - NetExec

Authentication syntax

```
$ netexec smb <IP> -u "<username>" -p "<password>" [-d <domain> | --local-auth]

$ netexec smb <IP> -u "<username>" -H "<nt_hash>" [-d <domain> | --local-auth]
```

### 1.6 - Mount Share

```
$ sudo mkdir /mnt/smb

$ sudo mount -t cifs //<IP>/<share_name> /mnt/smb

$ sudo mount -t cifs -o "port=<PORT> username=<username>,password=<password>" //<IP>/<share_name> /mnt/smb
```

## 02 - System Volume Information

```
$ smbclient -U "[<domain>/]<username>%<password>" //<IP>/SYSVOL

$ smbclient -U "[<domain>/]<username>" -hashes :<nt_hash> //<IP>/SYSVOL

smb: \> ls
```

---
## References

- [Enum4Linux-NG](https://github.com/cddmp/enum4linux-ng)