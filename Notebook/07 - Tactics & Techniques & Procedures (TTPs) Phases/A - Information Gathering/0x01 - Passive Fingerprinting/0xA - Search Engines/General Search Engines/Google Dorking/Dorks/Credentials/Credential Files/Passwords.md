# Passwords

## Files

```
userpass.txt
creds.txt
share.passwd
cloud.passwd
ftp.passwd
```

## Environment Files

```
filetype:env "DB_PASSWORD"
```

## HTPasswd

```
inurl:htpasswd ext:txt
filetype:htpasswd htpasswd
filetype:htpasswd inurl:htpasswd
```

## Generic

```
intitle:index.of "<filename>.txt"

intitle:"index of" share.passwd OR cloud.passwd OR ftp.passwd - public

intitle:"index of" share.passwd OR cloud.passwd OR ftp.passwd - public
```

## Mail Server

```
passwords site:mail.<domain>.<tld>
```