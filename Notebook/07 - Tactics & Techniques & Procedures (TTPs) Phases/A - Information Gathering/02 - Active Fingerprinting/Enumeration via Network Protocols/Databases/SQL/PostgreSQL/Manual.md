# Manual

## 01 - Manual

TODO: Fill this information by referring to the references down below

### 1.1 - Usage

#### 1.1.1 - Authenticate

- Local

`$ psql -U <username>`

`$ psql -U <username> -W`

- Remote

`$ psql -h <IP> -U <username> -W`

`$ psql postgresql://<username>:<password>@<IP>:<PORT>/<database_name>`

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

### 1.2 - PostgreSQL Version

### 1.3 - Operating System

### 1.4 - Database

#### 1.4.1 - Retrieve Databases

#### 1.4.2 - Retrieve Tables

#### 1.4.3 - Hashdump

`postgres=# SELECT username, passwd FROM pg_shadow;`

---
## References

- [A Penetration Testers guide to PostgreSQL](https://medium.com/@cryptocracker99/a-penetration-testers-guide-to-postgresql-d78954921ee9)

- [Ultimate guide PostgreSQL Pentesting](https://medium.com/@lordhorcrux_/ultimate-guide-postgresql-pentesting-989055d5551e)

- [Hacking Articles: Pentration Testing on PostgreSQL 5432](https://www.hackingarticles.in/penetration-testing-on-postgresql-5432/)

- [Pentest Wiki: Database Assessment PostgreSQL](https://github.com/nixawk/pentest-wiki/blob/master/2.Vulnerability-Assessment/Database-Assessment/postgresql/postgresql_hacking.md)