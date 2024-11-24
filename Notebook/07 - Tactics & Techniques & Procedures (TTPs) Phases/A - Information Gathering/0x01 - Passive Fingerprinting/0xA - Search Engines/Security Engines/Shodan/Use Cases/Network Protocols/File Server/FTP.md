# FTP

## Anonymous Login

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

## Default Passwords

```
"default password" port:21
```

## RCE

```
vsftpd 2.3.4
"220 ProFTPD 1.3.5"
```