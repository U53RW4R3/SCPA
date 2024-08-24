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

### 2.2 - Nmap

```
$ sudo nmap -p 11211 -Pn -n -sV <IP>
```

## 03 - Enumerate incoming connections

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
msf > use auxiliary/gather/memcached_extractor
msf auxiliary(gather/memcached_extractor) > options

Module options (auxiliary/gather/memcached_extractor):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target address range or CIDR identifier
   RPORT    11211            yes       The target port (TCP)
   THREADS  1                yes       The number of concurrent threads

msf auxiliary(gather/memcached_extractor) > set rhosts <IP>

msf auxiliary(gather/memcached_extractor) > set threads <int>

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

- [Hacktricks: Pentesting Memcache](https://book.hacktricks.xyz/network-services-pentesting/11211-memcache)

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/04 - Vulnerable Network Protocols/Remote Services/Memcached|Vulnerability Assessment: Memcached]]