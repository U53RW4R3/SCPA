---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - command-and-control
  - metasploit-framework
---
# Installation

## 01 - Package Manager

Install it according to your package manager.

```
$ yay -S metasploit
```

## 02 - Universal Installation

### 2.1 - Installer

```
# curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall

# wget -qO msfinstall https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb
```

Execute the script to install Metasploit.

```
# chmod 755 msfinstall && ./msfinstall
```

### 2.2 - Container

```
$ docker pull metasploitframework/metasploit-framework

$ docker run --rm -it -p 443:443 -v $PWD:/root/.msf4/ metasploitframework/metasploit-framework
```

## 03 - Setup Database

TODO: Fill this info

```
userware@hackware-os:~$ sudo -s

root@hackware-os:~# su postgres

postgres@hackware-os:/home/user$ psql

postgres=# CREATE USER <username> WITH PASSWORD '<password>';
postgres=# CREATE DATABASE <database_name> OWNER <username>;
postgres=# \q
exit
```

```
root@hackware-os:~# cat > /opt/metasploit-framework/database.yml << EOF
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

root@hackware-os:~# sh -c "echo export MSF_DATABASE_CONFIG=/opt/metasploit-framework/database.yml >> ~/.bashrc"
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