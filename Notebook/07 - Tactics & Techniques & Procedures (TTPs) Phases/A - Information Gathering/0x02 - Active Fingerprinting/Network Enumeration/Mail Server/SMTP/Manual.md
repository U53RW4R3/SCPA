# Manual

## 01 - Banner Grab or Establish Connection

### 1.1 - SMTP

```
$ nc -nv <IP> 25
```

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

## 04 - Username Bruteforce Enumeration

Note: Authenticating with SMTP protocols is not often required

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

---
## References

- [Hacktricks: Pentesting SMTP](https://book.hacktricks.xyz/pentesting/pentesting-smtp)

- [Hacktricks: SMTP Commands](https://book.hacktricks.xyz/pentesting/pentesting-smtp/smtp-commands)