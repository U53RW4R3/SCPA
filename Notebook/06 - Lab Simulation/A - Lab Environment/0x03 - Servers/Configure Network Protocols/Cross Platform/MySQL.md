# MySQL

Install the required packages.

```
$ sudo apt install mariadb-server mariadb-client
```

Open port 3306 to all network interfaces.

```
$ cat /etc/mysql/mariadb.conf.d/50-server.cnf
port                    = 3306
..[omitted]..
bind-address            = 0.0.0.0

$ sudo systemctl restart mysql
```