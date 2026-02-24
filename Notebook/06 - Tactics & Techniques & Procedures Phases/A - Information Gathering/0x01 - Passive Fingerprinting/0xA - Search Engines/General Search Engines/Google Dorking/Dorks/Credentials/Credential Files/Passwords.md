# Passwords

## Database

```
filetype:properties inurl:db intext:password
```

## Environment Files

```
filetype:env "DB_USERNAME"
filetype:env=v "DB_PASSWORD"

ext:ini intext:env.ini
```

## Files

```
userpass.txt
creds.txt
share.passwd
cloud.passwd
ftp.passwd
```

## Frontpage

```
intext:" -FrontPage-" ext:pwd inurl:(service | authors | administrators | users)
```

## Generic

```
intitle:index.of "<filename>.txt"

intitle:"index of" share.passwd OR cloud.passwd OR ftp.passwd - public

intitle:"index of" share.passwd OR cloud.passwd OR ftp.passwd - public
```

Windows registry files

```
filetype:reg reg +intext:"defaultusername" +intext:"defaultpassword"
```

## HTPasswd

```
inurl:htpasswd ext:txt
filetype:htpasswd htpasswd
filetype:htpasswd inurl:htpasswd
```

## Mail Server

```
passwords site:mail.<domain>.<tld>
```