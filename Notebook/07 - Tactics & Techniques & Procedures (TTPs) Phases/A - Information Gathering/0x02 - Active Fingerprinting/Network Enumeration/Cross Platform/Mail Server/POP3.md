---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - pop3
  - network-mapper
  - metasploit-framework
---
# POP3

## 01 - Banner Grab

### 1.1 - Manual

```
$ nc -nv <IP> 110

$ openssl s_client -connect <IP>:995 -crlf -quiet
```

### 1.2 - Network Mapper

TODO: Create headers to each commands.

```
$ nmap -p 110,995 -sV --script pop3-capabilities <IP>
```

```
$ nmap -p 110,995 -sV --script pop3-ntlm-info <IP>
```

### 1.3 - Metasploit

```
msf > use auxiliary/scanner/pop3/pop3_version

msf auxiliary(scanner/pop3/pop3_version) > options

Module options (auxiliary/scanner/pop3/pop3_version):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    110              yes       The target port (TCP) 
   THREADS  1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/pop3/pop3_version) > set rhosts <IP>

msf auxiliary(scanner/pop3/pop3_version) > set threads 4

msf auxiliary(scanner/pop3/pop3_version) > run -j
```

---
## References

- [Hacktricks: Pentesting POP](https://book.hacktricks.xyz/pentesting/pentesting-pop)