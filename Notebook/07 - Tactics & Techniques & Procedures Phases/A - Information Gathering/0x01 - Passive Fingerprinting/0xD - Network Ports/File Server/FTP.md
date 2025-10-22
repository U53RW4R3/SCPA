# FTP

## Anonymous Login

Shodan

```
port:21 230

ftp 230 -unknown -print

"Anonymous+access+allowed" connected -530

port:21 "220" "230 Login successful."

port:21 230 Any password will work

230 'anonymous@' login ok

220 ProFTPD Server "anonymous+access+granted"

port:21 User logged in product:"Microsoft ftpd"
```

Github

```
/ftp:\/\/.*:.*@.*domain\.tld/
ftp_host=
FTP_LOGIN=
FTP_PASSWORD=
FTP_PW=
FTP_USER=
ftp_username=
```

## Default Passwords

Shodan

```
"default password" port:21
```

## RCE

Shodan

```
vsftpd 2.3.4
"220 ProFTPD 1.3.5"
```