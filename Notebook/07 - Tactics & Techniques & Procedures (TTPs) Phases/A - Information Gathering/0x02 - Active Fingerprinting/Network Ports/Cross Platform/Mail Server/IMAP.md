---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - imap
  - network-mapper
  - metasploit-framework
---
# IMAP

## 01 - Banner Grab

### 1.1 - Manual

```
$ nc -nv <IP> 143

$ openssl s_client -connect <IP>:993 -quiet
```

### 1.2 - Network Mapper

```
$ nmap -p 143,993 -Pn -n -sV <IP>

$ nmap -p 143,993 -sV --script imap-capabilities <IP>
```

### 1.3 - Metasploit

```
msf > use auxiliary/scanner/imap/imap_version

msf auxiliary(scanner/imap/imap_version) > options

Module options (auxiliary/scanner/imap/imap_version):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   IMAPPASS                   no        The password for the specified username
   IMAPUSER                   no        The username to authenticate as
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     143              yes       The target port (TCP)
   THREADS   1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/imap/imap_version) > set rhosts <IP>

msf auxiliary(scanner/imap/imap_version) > set threads 4

msf auxiliary(scanner/imap/imap_version) > set imapuser <username>

msf auxiliary(scanner/imap/imap_version) > set imappass <password>

msf auxiliary(scanner/imap/imap_version) > run -j
```

## 02 - Check Remote Certificates

```
$ openssl s_client -showcerts -starttls imap -connect <IP>:139
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/03 - Network Ports/Mail Server/IMAP]]

### Hacktricks

- [Hacktricks: Pentesting IMAP](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-imap.html)