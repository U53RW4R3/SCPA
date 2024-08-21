# PostgreSQL

## 01 - Banner Grab

### 1.1 - Nmap

```
$ nmap -p 5432 -Pn -n -sV --script banner <IP>
```

### 1.2 - Metasploit

```
msf > use auxiliary/scanner/postgres/postgres_version

msf auxiliary(scanner/postgres/postgres_version) > options

Module options (auxiliary/scanner/postgres/postgres_version):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   DATABASE  template1        yes       The database to authenticate against
   PASSWORD  postgres         no        The password for the specified username. Leave blank for a random password.
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     5432             yes       The target port
   THREADS   1                yes       The number of concurrent threads (max one per host)
   USERNAME  postgres         yes       The username to authenticate as
   VERBOSE   false            no        Enable verbose output

msf auxiliary(scanner/postgres/postgres_version) > set database <database_name>

msf auxiliary(scanner/postgres/postgres_version) > run postgres://<username>:<password>@<IP> threads=8
```

## 02 - Authenticate

- Local

```
$ psql -U <username>

$ psql -U <username> -W
```

- Remote

```
$ psql -h <IP> -U <username> -W

$ psql postgresql://<username>:<password>@<IP>:<PORT>/<database_name>
```


---
## References

- [A Penetration Testers guide to PostgreSQL](https://medium.com/@cryptocracker99/a-penetration-testers-guide-to-postgresql-d78954921ee9)

- [Ultimate guide PostgreSQL Pentesting](https://medium.com/@lordhorcrux_/ultimate-guide-postgresql-pentesting-989055d5551e)

- [Hacking Articles: Pentration Testing on PostgreSQL 5432](https://www.hackingarticles.in/penetration-testing-on-postgresql-5432/)

- [Metasploit Unleashed: Admin Postgre Auxiliary Module](https://www.offsec.com/metasploit-unleashed/admin-postgres-auxiliary-modules/)

- [Pentest Wiki: Database Assessment PostgreSQL](https://github.com/nixawk/pentest-wiki/blob/master/2.Vulnerability-Assessment/Database-Assessment/postgresql/postgresql_hacking.md)