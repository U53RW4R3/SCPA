---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - memcached
  - network-mapper
  - metasploit-framework
---
# Memcached

## 01 - Setup

```
$ sudo apt install libmemcached-tools
```

## 02 - Banner Grab

### 2.1 - Manual

Using `netcat` to grab the service version number.

```
$ nc <IP> 11211
```

Using `telnet` to grab the service version number.

```
$ telnet <IP> 11211
version
```

### 2.2 - Network Mapper

```
$ sudo nmap -p 11211 -Pn -n -sV <IP>
```

## 03 - Enumerate Incoming Connections

```
$ nmap -p 11211 -Pn -n --script memcached-info <IP>
```

## 04 - Enumerate Items

```
$ memcstat --servers=<IP> [--username=<password> --password=<password>]
..[omitted]..
curr_items: <int>
..[omitted]..
```

## 05 - Extract Data

### 5.1 - Dump the keys

#### 5.1.1 - Manual

```
$ memcdump --server=<IP> [--username=<password> --password=<password>]
```

#### 5.1.2 - Metasploit

```
msf > use auxiliary/gather/memcached_extractors

msf auxiliary(gather/memcached_extractor) > options

Module options (auxiliary/gather/memcached_extractor):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target address range or CIDR identifier
   RPORT    11211            yes       The target port (TCP)
   THREADS  1                yes       The number of concurrent threads

msf auxiliary(gather/memcached_extractor) > set rhosts <IP>

msf auxiliary(gather/memcached_extractor) > set threads <threads>

msf auxiliary(gather/memcached_extractor) > run
```

### 5.2 - Enumerate Keys

```
$ /usr/share/memcached/scripts/memcached-tool <IP>:11211 dump [key_name]
```

Display the key's values

```
$ memccat --server=<IP> [--username=<password> --password=<password>] <key_name_1> <key_name_n>
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/03 - Network Ports/Remote Services/Memcached|Vulnerability Assessment: Memcached]]

### Hacktricks

- [Hacktricks: Pentesting Memcache](https://book.hacktricks.wiki/en/network-services-pentesting/11211-memcache/memcache-commands.html)