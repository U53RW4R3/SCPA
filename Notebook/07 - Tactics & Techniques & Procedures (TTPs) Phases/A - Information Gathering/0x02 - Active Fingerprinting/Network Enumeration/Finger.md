# Finger

## 01 - Banner Grab

```
$ nc -nv <IP> 79

$ echo "root" | nv -nv <IP> 79
```

## 02 - User Enumeration

### 2.1 - Manual

```
$ finger @<IP>

$ finger <username>@<IP>
```

### 2.2 - `finger-user-enum.pl`

```
$ finger-user-enum.pl -U users.lst -t <IP>

$ finger-user-enum.pl -u <username> -t <IP>

$ finger-user-enum.pl -U users.lst -T ip_targets.txt
```

### 2.3 - Nmap

```
$ sudo nmap -p 79 -Pn -n -sV --script finger <IP>
```

### 2.4 - Metasploit

```
msf > use auxiliary/scanner/finger/finger_users

msf auxiliary(scanner/finger/finger_users) > options

Module options (auxiliary/scanner/finger/finger_users):

   Name        Current Setting                                Required  Description 
   ----        ---------------                                --------  ----------- 
   RHOSTS                                                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit 
   RPORT       79                                             yes       The target port (TCP) 
   THREADS     1                                              yes       The number of concurrent threads (max one per host) 
   USERS_FILE  /opt/metasploit/data/wordlists/unix_users.txt  yes       The file that contains a list of default UNIX accounts.

msf auxiliary(scanner/finger/finger_users) > set rhosts <IP>

msf auxiliary(scanner/finger/finger_users) > run
```

---
## References

- [Hacktricks: Pentesting Finger](https://book.hacktricks.xyz/pentesting/pentesting-finger)

- [PentestMonkey: Finger-User-Enum](https://pentestmonkey.net/tools/user-enumeration/finger-user-enum)