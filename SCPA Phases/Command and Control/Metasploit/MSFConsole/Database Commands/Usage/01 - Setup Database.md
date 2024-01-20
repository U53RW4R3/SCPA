# 01 - Setup Database

TODO: Fill this info

```
user@pentestos:~$ sudo -s

root@pentestos:~# su postgres

postgres@pentestos:/home/user$ psql

postgres=# CREATE USER <username> WITH PASSWORD '<password>';
postgres=# CREATE DATABASE <database_name> OWNER <username>;
postgres=# \q
exit
```

```
root@pentestos:~# cat > /opt/metasploit-framework/database.yml << EOF
production:
    adapter: postgresql
    database: <database_template>
    username: <username>
    password: <password>
    host: localhost
    port: 5432
    pool: 75
    timeout: 5
EOF

root@pentestos:~# sh -c "echo export MSF_DATABASE_CONFIG=/opt/metasploit-framework/database.yml >> ~/.bashrc"
```

```
$ sudo msfconsole -q
```

- Optionally you can connect it manually

```
msf > db_connect /opt/metasploit-framework/database.yml

msf > db_connect <username>:<password>[@<IP>:<PORT>/<database_template>]
```

- Run to see if you're connected to the database

```
msf > db_status
```

---
## References

- [Metasploit Postgres Setup](https://fedoraproject.org/wiki/Metasploit_Postgres_Setup)