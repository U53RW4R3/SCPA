---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - ssh
---
# SSH

## 01 - Banner Grab

### 1.1 - Manual

#### 1.1.1 - #ncat

```
$ echo "EXIT" | ncat -nv <IP> 22
```

#### 1.1.2 - Telnet

```
$ echo "EXIT" | telnet <IP> 22
```

### 1.2 - #metasploit

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

### 2.1 - Manual

Check what SSH authentication methods are available. If it has a `password` authentication method is enabled then start [[07 - Tactics & Techniques & Procedures Phases/B - Vulnerability Assessment/0x03 - Network Ports/Remote Services/SSH#^664b04|brute forcing]].

```
$ ssh -v <IP>
..[omitted]..
debug1: Authentications that can continue: publickey,password,keyboard-interactive
```

> [!INFO]
> If the authentication limit is **configured to fail** and it couldn't display a remote password prompt. You can force it with the `PreferredAuthentications` option.

```
$ ssh -v <IP> -o PreferredAuthentications=password
..[omitted]..
debug1: Next authentication method: password
```

### 2.2 - #network-mapper

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

- [[07 - Tactics & Techniques & Procedures Phases/B - Vulnerability Assessment/0x03 - Network Ports/Remote Services/SSH|Vulnerability Assessment: SSH]]

### Source Repositories

- [SSH-Audit](https://github.com/jtesta/ssh-audit)

### Hacktricks

^61f7a9

- [Hacktricks: Pentesting SSH](https://hacktricks.wiki/en/network-services-pentesting/pentesting-ssh.html) ^67ec6f

### Hacking Articles

^446086

- [Hacking Articles: SSH Penetration Testing](https://www.hackingarticles.in/ssh-penetration-testing-port-22/) ^d90b90

### 0xffsec

- [0xffsec: SSH Legacy Key Exchange Algorithm](https://0xffsec.com/handbook/notes/ssh-legacy-key-exchange/)

### Kali Documentation

- [Kali Docs: SSH Configuration](https://www.kali.org/docs/general-use/ssh-configuration/)