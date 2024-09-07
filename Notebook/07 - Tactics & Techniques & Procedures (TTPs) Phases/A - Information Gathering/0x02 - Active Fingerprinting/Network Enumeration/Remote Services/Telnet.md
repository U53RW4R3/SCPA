# Telnet

## 01 - Manual

### 1.1 - Banner Grab

```
$ nc -nv <IP> 23
```

## 02 - Network Mapper

```
$ nmap -p 23 -n -sV -Pn --script telnet-encryption <IP>

$ nmap -p 23 -n -sV -Pn --script telnet-ntlm-info <IP>
```

## 03 - Metasploit

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

---
## References

- [Pentesting Telnet](https://book.hacktricks.xyz/pentesting/pentesting-telnet)