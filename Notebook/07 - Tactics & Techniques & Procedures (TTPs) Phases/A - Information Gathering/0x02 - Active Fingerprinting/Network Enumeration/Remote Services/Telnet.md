---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - telnet
  - network-mapper
  - metasploit-framework
---
# Telnet

## 01 - Banner Grab

### 1.1 - Manual

```
$ nc -nv <IP> 23
```

### 1.2 - Network Mapper

```
$ nmap -p 23 -n -Pn -sV <IP>
```

### 1.3 - Metasploit

```
msf > use auxiliary/scanner/telnet/telnet_version

msf auxiliary(scanner/telnet/telnet_version) > options

Module options (auxiliary/scanner/telnet/telnet_version):

   Name      Current Setting  Required  Description 
   ----      ---------------  --------  ----------- 
   PASSWORD                   no        The password for the specified username 
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     23               yes       The target port (TCP) 
   THREADS   1                yes       The number of concurrent threads (max one per host) 
   TIMEOUT   30               yes       Timeout for the Telnet probe 
   USERNAME                   no        The username to authenticate as 

msf auxiliary(scanner/telnet/telnet_version) > set rhosts <IP>

msf auxiliary(scanner/telnet/telnet_version) > set threads 8

msf auxiliary(scanner/telnet/telnet_version) > run
```

## 02 - RDP Encryption Algorithm

```
$ nmap -p 23 -n -Pn --script telnet-encryption <IP>
```

## 03 - NTLM Information

```
$ nmap -p 23 -n -Pn --script telnet-ntlm-info <IP>
```

---
## References

- [Pentesting Telnet](https://book.hacktricks.xyz/pentesting/pentesting-telnet)