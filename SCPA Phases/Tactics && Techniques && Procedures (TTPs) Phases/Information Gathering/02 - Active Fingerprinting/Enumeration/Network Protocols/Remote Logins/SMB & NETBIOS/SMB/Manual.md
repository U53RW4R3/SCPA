# Manual

## 01 - Usage

### 1.1 - Samba Suite Utils

```
$ smbclient -U "<username>%<password>" -L //<IP>

$ smbclient -U "<username>" --password="<password>" -L //<IP>

$ smbclient -U "<username>" --pw-nt-hash <nt_hash> -L //<IP>

$ pth-smbclient -U <domain>/<username>%aad3b435b51404eeaad3b435b51404ee:<nt_hash> //<IP>/c$

$ smbclient --option="client min protocol=core" -U "" //<IP>/<share>
```

### 1.2 - Impacket

```
$ smbclient.py [<domain>/]<username>:<password>@<IP>

$ smbclient.py -hashes :<nt_hash> [<domain>/]<username>@<IP>
```

### 1.3 - SMBMap

- Authenticate

`$ smbmap -u "<username>" -p "<password>" -H <IP> [-P <PORT>]`

- Pass the hash

`$ smbmap -u "<username>" -p "<NT>:<LM>" -H <IP> [-P <PORT>]`

### 1.4 - Enum4Linux

`$ enum4linux -a -u "<username>" -p "<password>" <IP>`

### 1.5 - NetExec

- Authenticate

`$ netexec smb <IP> -u "<username>" -p "<password>" --groups --local-groups --loggedon-users --rid-brute --sessions --users --shares --pass-pol`

- Pass The Hash

`$ netexec smb <IP> -u "<username>" -H "<nt_hash>" --groups --local-groups --loggedon-users --rid-brute --sessions --users --shares --pass-pol`

### 1.6 - Mount Share

`$ sudo mkdir /mnt/smb`

`$ sudo mount -t cifs //<IP>/<share_name> /mnt/smb`

`$ sudo mount -t cifs -o "port=<PORT> username=<username>,password=<password>" //<IP>/<share_name> /mnt/smb`

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

### 2.5 - netexec

```
$ netexec smb <IP> -u "" -p "" --shares

$ netexec smb <IP> -u "guest" -p "" --shares
```

## 03 - System Volume Information

### 3.1 - Samba Suite Utils

```
$ smbclient -U "<username>%<password>" //<domain_name/SYSVOL

smb: \> ls
```