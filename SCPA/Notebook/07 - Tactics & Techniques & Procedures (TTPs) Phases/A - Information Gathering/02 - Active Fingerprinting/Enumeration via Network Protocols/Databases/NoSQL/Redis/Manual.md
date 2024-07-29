# Manual

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

## 02 - No Authentication

### 2.1 - Netcat

```
$ nc <IP> 6379 -v
```

---
## References

 - [Hacktricks: Pentesting Redis](https://book.hacktricks.xyz/network-services-pentesting/6379-pentesting-redis)