---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - ftp
  - network-mapper
  - metasploit-framework
---
# FTP

## 01 - Banner Grab

### 1.1 - Manual

```
$ nc -nv <IP> 21

$ telnet -n <IP> 21
```

### 1.2 - Metasploit

```
msf > use auxiliary/scanner/ftp/ftp_version

msf auxiliary(scanner/ftp/ftp_version) > options

Module options (auxiliary/scanner/ftp/ftp_version):

   Name     Current Setting      Required  Description 
   ----     ---------------      --------  ----------- 
   FTPPASS  mozilla@example.com  no        The password for the specified username 
   FTPUSER  anonymous            no        The username to authenticate as 
   RHOSTS                        yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    21                   yes       The target port (TCP) 
   THREADS  1                    yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/ftp/ftp_version) > set rhosts <IP>

msf auxiliary(scanner/ftp/ftp_version) > set threads 8

msf auxiliary(scanner/ftp/ftp_version) > run
```

## 02 - Retrieve a certificate if any

```
$ openssl s_client -connect <IP>:21 -starttls ftp
```

## 03 - Enumerate Operating System

### 3.1 - Manual

```
ftp> SYST

ftp> STAT
```

### 3.2 - Network Mapper

```
$ nmap -p 21 -sV --script ftp-syst <IP>
```

## 04 - Authenticate FTP server

### 4.1 - Basic

```
$ ftp <IP> [-P <PORT>]

$ ftp -u ftp://<username>:<password>@<IP>[:PORT]
```

Web browser connection

```
ftp://<username>:<password>@<IP>
```

### 4.2 - Login using startTLS

Install a sophisticated CLI based FTP client in Debian-based distros.

```
$ sudo apt install lftp
```

Install a sophisticated CLI based FTP client in Arch Linux-based distros.

```
$ sudo pacman -S lftp
```

CLI syntax usage.

```
$ lftp
lftp :~> set ftp:ssl-force true
lftp :~> set ssl:verify-certificate no
lftp :~> connect <IP>
lftp <IP>:~> login
Usage: login <user|URL> [<pass>]

$ lftp [-p <PORT>] -e "set ssl:verify-certificate false" -u "<username>,<password>" <IP>
```

## 05 - Basic Commands

List files and directories including hidden ones

```
ftp> ls -a
```

Set file transfers mode as binary

```
ftp> binary
```

Set file transfers mode as ascii

```
ftp> ascii
```

Disconnect FTP server

```
ftp> <exit | quit | bye>
```

## 06 - Enumerate Files

```
$ curl ftp://<username>@<password>@<IP>/

$ curl --list-only ftp://<username>@<password>@<IP>/
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/B - Vulnerability Assessment/0x03 - Network Ports/File Server/FTP]]

### Hacktricks

- [Hacktricks: Pentesting FTP](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-ftp/index.html)