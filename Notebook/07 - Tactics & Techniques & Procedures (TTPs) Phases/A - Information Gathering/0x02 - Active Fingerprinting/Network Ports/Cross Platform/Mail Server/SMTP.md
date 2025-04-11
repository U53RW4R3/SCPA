---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - smtp
  - network-mapper
  - metasploit-framework
---
# SMTP

## 01 - Banner Grab

### 1.1 - SMTP

#### 1.1.1 - Manual

```
$ nc -nv <IP> 25
```

#### 1.1.2 - Metasploit

```
msf > use auxiliary/scanner/smtp/smtp_version

msf auxiliary(scanner/smtp/smtp_version) > options

Module options (auxiliary/scanner/smtp/smtp_version):

   Name     Current Setting  Required  Description 
   ----     ---------------  --------  ----------- 
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    25               yes       The target port (TCP) 
   THREADS  1                yes       The number of concurrent threads (max one per host) 

msf auxiliary(scanner/smtp/smtp_version) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_version) > set threads 10

msf auxiliary(scanner/smtp/smtp_version) > run
```

Enumerating the domain controller.

```
msf > use auxiliary/scanner/smtp/smtp_ntlm_domain

msf auxiliary(scanner/smtp/smtp_ntlm_domain) > options

Module options (auxiliary/scanner/smtp/smtp_ntlm_domain):

   Name         Current Setting  Required  Description
   ----         ---------------  --------  -----------
   EHLO_DOMAIN  localhost        yes       The domain to send with the EHLO command
   RHOSTS                        yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT        25               yes       The target port (TCP)
   THREADS      1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smtp/smtp_ntlm_domain) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_ntlm_domain) > set ehlo_domain <domain>

msf auxiliary(scanner/smtp/smtp_ntlm_domain) > run
```

^ef9d56

### 1.2 - SMTPS (Secure protocol that contains SSL/TLS)

For port 465 without the `starttls` command

```
$ openssl s_client -crlf -connect <smtp_mail_server>:465
```

For port 587

```
$ openssl s_client -starttls smtp -crlf -connect <smtp_mail_server>:587
```

## 02 - Search for MX servers of an organization you're targeting

```
$ dig +short mx <target.com>
```

## 03 - NTLM Auth - Information Disclosure

```
$ telnet <ip> 587
220 <IP> SMTP Server Banner
>> HELO
250 <IP> Hello [x.x.x.x]
>> AUTH NTLM 334
NTLM supported
>> TlRMTVNTUAABAAAAB4IIAAAAAAAAAAAAAAAAAAAAAAA=
334 TlRMTVNTUAACAAAACgAKADgAAAAFgooCBqqVKFrKPCMAAAAAAAAAAEgASABCAAAABgOAJQAAAA9JAEkAUwAwADEAAgAKAEkASQBTADAAMQABAAoASQBJAFMAMAAxAAQACgBJAEkAUwAwADEAAwAKAEkASQBTADAAMQAHAAgAHwMI0VPy1QEAAAAA
```

## 04 - Username Brute Force Enumeration

> [!NOTE]
> Authenticating with SMTP protocols often not required.

### 4.1 - Manual Enumeration

#### 4.1.1 - RCPT TO

```
$ telnet <IP> 25
Trying <IP>...
Connected to <IP>.
Escape character is '^]'
220 myhost ESMTP Sendmail 8.9.3
HELO x
250 myhost Hello [<another_IP>], pleased to meet you
MAIL FROM:test@test.org
250 2.1.0 test@test.org... Sender ok
RCPT TO:test
550 5.1.1 test... User unknown
RCPT TO:admin
550 5.1.1 admin... User unknown
RCPT TO:ed
250 2.1.5 ed... Recipient ok
```

#### 4.1.2 - VRFY

```
$ telnet <IP> 25
Trying <IP>...
Connected to <IP>.
Escape character is '^]'
220 myhost ESMTP Sendmail 8.9.3
HELO
501 HELO requires domain address
HELO x
250 myhost Hello [<another_IP>], pleased to meet you
VRFY root
250 Super-User <root@myhost>
VRFY blah
550 blah... User unknown
```

#### 4.1.3 - EXPN

```
$ telnet <IP> 25
Trying <IP>...
Connected to <IP>.
Escape character is '^]'
220 myhost ESMTP Sendmail 8.9.3
HELO
501 HELO requires domain address
HELO x
EXPN test
550 5.1.1 test... User unknown
EXPN root
250 2.1.5 <ed.williams@myhost>
EXPN sshd
250 2.1.5 sshd privsep <sshd@mail2>
```

### 4.2 - Automated Enumeration

#### 4.2.1 - Python script

```python
#!/usr/bin/env python3
import socket
import sys

username = sys.argv[1]
host = sys.argv[2]

if len(sys.argv) != 3:
    print("Usage: %s <username> <IP>" % sys.argv[0])
    sys.exit(0)

# Create a socket and connect to the server
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
connect = sock.connect((host, 25))

# Receive the banner
banner = sock.recv(1024)
print(banner)

# VRFY a user
sock.send('VRFY ' + username + '\r\n')
output = sock.recv(1024)
print(output)

# Close the socket
sock.close()
```

The syntax as it follows.

```
$ chown 755 vrfy.py

$ ./vrfy.py <username> <IP>
```

#### 4.2.2 - `smtp-user-enum`

```
$ smtp-user-enum -M <MODE> -u <USER> -t <IP>
```

#### 4.2.3 - `nmap`

```
$ nmap -p 25 -Pn --script smtp-commands,smtp-strangeport <IP>

$ nmap -p 25 -Pn --script smtp-enum-users <IP>

$ nmap -p 587 -Pn --script smtp-ntlm-info <IP>
```

#### 4.2.4 - `patator`

TODO: Fill this info

```
$ patator
```

+ smtp_vrfy     : Enumerate valid users using SMTP VRFY
+ smtp_rcpt     : Enumerate valid users using SMTP RCPT TO

#### 4.2.5 - Metasploit

```
msf > use auxiliary/scanner/smtp/smtp_enum

msf auxiliary(scanner/smtp/smtp_enum) > options

Module options (auxiliary/scanner/smtp/smtp_enum):

   Name       Current Setting                                                Required  Description
   ----       ---------------                                                --------  -----------
   RHOSTS                                                                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      25                                                             yes       The target port (TCP)
   THREADS    1                                                              yes       The number of concurrent threads (max one per host)
   UNIXONLY   true                                                           yes       Skip Microsoft bannered servers when testing unix users
   USER_FILE  /usr/share/metasploit-framework/data/wordlists/unix_users.txt  yes       The file that contains a list of probable users accounts.

msf auxiliary(scanner/smtp/smtp_enum) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_enum) > set threads 256

msf auxiliary(scanner/smtp/smtp_enum) > run
```

## 05 - SMTP Relay

Check for open SMTP relays that can be used to create a spoofed email when planning a spear phishing attempt.

```
msf > use auxiliary/scanner/smtp/smtp_relay

msf auxiliary(scanner/smtp/smtp_relay) > options

Module options (auxiliary/scanner/smtp/smtp_relay):

   Name      Current Setting     Required  Description
   ----      ---------------     --------  -----------
   EXTENDED  false               yes       Do all the 16 extended checks
   MAILFROM  sender@example.com  yes       FROM address of the e-mail
   MAILTO    target@example.com  yes       TO address of the e-mail
   RHOSTS                        yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     25                  yes       The target port (TCP)
   THREADS   1                   yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smtp/smtp_relay) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_relay) > set mailfrom <sender_email@target.com>

msf auxiliary(scanner/smtp/smtp_relay) > set mailto <victim@target.com>

msf auxiliary(scanner/smtp/smtp_relay) > set threads 2 <IP>

msf auxiliary(scanner/smtp/smtp_relay) > set extended <true | false>

msf auxiliary(scanner/smtp/smtp_relay) > exploit -j
```

---
## References

### Hacktricks

- [Hacktricks: Pentesting SMTP](https://book.hacktricks.wiki/en/pentesting/pentesting-smtp.html)

- [Hacktricks: SMTP Commands](https://book.hacktricks.wiki/en/pentesting/pentesting-smtp/smtp-commands.html)

### Black Hills Information Security

- [Black Hills Information Security: How to Test for Open Mail Relays](https://www.blackhillsinfosec.com/how-to-test-for-open-mail-relays/)