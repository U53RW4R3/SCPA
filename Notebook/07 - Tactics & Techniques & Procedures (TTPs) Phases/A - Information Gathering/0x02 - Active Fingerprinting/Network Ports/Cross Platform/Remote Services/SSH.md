---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - ssh
  - network-mapper
  - metasploit-framework
---
# SSH

## 01 - Banner Grab

### 1.1 - Manual

#### 1.1.1 - Ncat

```
$ echo "EXIT" | ncat -nv <IP> 22
```

#### 1.1.2 - Telnet

```
$ echo "EXIT" | telnet <IP> 22
```

### 1.2 - Metasploit

```
msf > use auxiliary/scanner/ssh/ssh_version

msf auxiliary(scanner/ssh/ssh_version) > options

Module options (auxiliary/scanner/ssh/ssh_version): 

   Name     Current Setting  Required  Description 
   ----     ---------------  --------  ----------- 
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit 
   RPORT    22               yes       The target port (TCP) 
   THREADS  1                yes       The number of concurrent threads (max one per host) 
   TIMEOUT  30               yes       Timeout for the SSH probe

msf auxiliary(scanner/ssh/ssh_version) > set rhosts <IP>

msf auxiliary(scanner/ssh/ssh_version) > set rport <PORT>

msf auxiliary(scanner/ssh/ssh_version) > set threads 8

msf auxiliary(scanner/ssh/ssh_version) > run
```

## 02 - SSH Authentication Methods

Check what SSH authentication methods are available. If it has a `password` authentication method is enabled then start [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/04 - Vulnerable Network Ports/Remote Services/TODO Sort it/SSH|brute forcing]].

```
$ nmap -p 22 --script ssh-auth-methods --script-args="ssh.user=<username>" <IP>
```

## 03 - Known Host Keys

```
$ nmap -p 22 --script ssh-hostkey --script-args ssh_hostkey=full <IP>

$ nmap -p 22 --script ssh-hostkey --script-args ssh_hostkey=all <IP>

$ nmap -p 22 --script ssh-hostkey --script-args ssh_hostkey='visual bubble' <IP>
```

## 04 - Algorithms

```
$ nmap -p 22 --script ssh2-enum-algos <IP>
```

## 05 - Automated

```
$ ssh-audit <IP>
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/03 - Network Ports/Remote Services/SSH|Vulnerability Assessment: SSH]]

### Github

- [SSH-Audit](https://github.com/jtesta/ssh-audit)

### Hacktricks

- [Hacktricks: Pentesting SSH](https://book.hacktricks.wiki/en/pentesting/pentesting-ssh.html)

### Hacking Articles

- [Hacking Articles: SSH Penetration Testing](https://www.hackingarticles.in/ssh-penetration-testing-port-22/)

### 0xffsec

- [0xffsec: SSH Legacy Key Exchange Algorithm](https://0xffsec.com/handbook/notes/ssh-legacy-key-exchange/)

### Kali Documentation

- [Kali Docs: SSH Configuration](https://www.kali.org/docs/general-use/ssh-configuration/)