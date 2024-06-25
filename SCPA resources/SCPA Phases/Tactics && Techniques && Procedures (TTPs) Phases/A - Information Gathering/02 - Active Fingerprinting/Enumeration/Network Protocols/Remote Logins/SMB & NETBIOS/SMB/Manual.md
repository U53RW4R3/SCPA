# Manual

## 01 - Usage

### 1.1 - Samba Suite Utils

#### 1.1.1 - Authentication

```
$ smbclient -U "<username>%<password>" -L //<IP>

$ smbclient -U "<username>" --password="<password>" -L //<IP>
```

- Pass The Hash

```
$ smbclient -U "<username>" --pw-nt-hash <nt_hash> -L //<IP>
```

- Set protocol

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

### 1.4 - Enum4Linux

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

```
$ enum4linux -a -u "<username>" -p "<password>" <IP>
```

https://juggernaut-sec.com/ad-recon-msrpc-over-smb/

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

## 02 - Anonymous Login

### 2.1 - Samba Suite Utils

```
$ smbclient -N -L //<IP>

$ smbclient -u "%" -L //<IP>

$ smbclient -u "guest%" -L //<IP>

$ smbclient -N -L //<IP> -mSMB2

$ smbclient -N -L //<IP> -mSMB3
```

### 2.2 - Impacket

TODO: Fill this info

```
$ smbclient.py -no-pass [<domain>/]''@<IP>

$ smbclient.py -no-pass [<domain>/]guest@<IP>
```

### 2.3 - SMBMap

```
$ smbmap -u "" -p "" -H <IP> [-P <PORT>]

$ smbmap -u "guest" -p "" -H <IP> [-P <PORT>]
```

### 2.4 - Enum4Linux

```
$ enum4linux -a -u "" -p "" <IP>

$ enum4linux -a -u "guest" -p "" <IP>
```

### 2.5 - NetExec

```
$ netexec smb <IP> -u "" -p "" [-d <domain> | --local-auth] --shares

$ netexec smb <IP> -u "guest" -p "" [-d <domain> | --local-auth] --shares
```

## 03 - System Volume Information

### 3.1 - Samba Suite Utils

```
$ smbclient -U "[<domain>/]<username>%<password>" //<IP>/SYSVOL

$ smbclient -U "[<domain>/]<username>" -hashes :<nt_hash> //<IP>/SYSVOL

smb: \> ls
```