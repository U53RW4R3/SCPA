# Nmap

## 01 - MySQL Information

```
$ nmap -p 3306 -sV --script mysql-info <IP>
```

## 02 - Empty Password

```
$ nmap -p 3306 --script mysql-empty-password <IP>
```

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

## 03 - MySQL Audit

```
$ nmap -p 3306 --script=mysql-audit --script-args="mysql-audit.username='<username>',mysql-audit.password='<password>',mysql-audit.filename='/usr/share/nmap/nselib/data/mysql-cis.audit'" <IP>
```