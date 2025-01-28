# RDP

## 01 - Banner Grab

### 1.1 - Nmap

```
$ nmap -p 3389 -Pn -sV <IP>
```

### 1.2 - Metasploit

```
msf > use auxiliary/scanner/rdp/rdp_scanner

msf auxiliary(scanner/rdp/rdp_scanner) > options

Module options (auxiliary/scanner/rdp/rdp_scanner):

   Name             Current Setting  Required  Description
   ----             ---------------  --------  -----------
   DETECT_NLA       true             yes       Detect Network Level Authentication (NLA)
   RDP_CLIENT_IP    192.168.0.100    yes       The client IPv4 address to report during connect
   RDP_CLIENT_NAME  rdesktop         no        The client computer name to report during connect, UNSET = random
   RDP_DOMAIN                        no        The client domain name to report during connect
   RDP_USER                          no        The username to report during connect, UNSET = random
   RHOSTS                            yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT            3389             yes       The target port (TCP)
   THREADS          1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/rdp/rdp_scanner) > set rhosts <target_IP>

msf auxiliary(scanner/rdp/rdp_scanner) > set threads 4

msf auxiliary(scanner/rdp/rdp_scanner) > set rdp_client_IP <client_IP>

msf auxiliary(scanner/rdp/rdp_scanner) > set rdp_client_name <client_name>

msf auxiliary(scanner/rdp/rdp_scanner) > run -j
```

## 02 - RDP Encryption Algorithm

```
$ nmap -p 3389 -Pn -sV --script rdp-enum-encryption <IP>
```

## 03 - NTLM Information

```
$ nmap -p 3389 -Pn -sV --script rdp-ntlm-info <IP>
```

---
## References

- [Hacktricks: Pentesting RDP](https://book.hacktricks.xyz/pentesting/pentesting-rdp)