# Redis

TODO: Fill this info

## 01 - Banner Grab

### 1.1 - Redis CLI

```
$ sudo apt install -y redis-tools

$ redis-cli -h <IP>
```

### 1.2 - Netcat

```
$ nc -vn <IP> 6379
```

```
$ nmap -p 6379 -Pn -n -sV --script 6379 <IP>
```

```
msf > use auxiliary/scanner/redis/redis_server

msf auxiliary(scanner/redis/redis_server) > options
```

---
## References

### Hacktricks

 - [Hacktricks: Pentesting Redis](https://book.hacktricks.wiki/en/network-services-pentesting/6379-pentesting-redis.html)