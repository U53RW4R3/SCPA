# Rsync

## Manual

```
$ rsync --list-only rsync://<IP>
```

## Network Mapper

```
$ nmap -p 873 -sV --script rsync-list-modules <IP>
```

## Metasploit

```
msf > use auxiliary/scanner/rsync/modules_list

msf auxiliary(scanner/rsync/modules_list) > options

msf auxiliary(scanner/rsync/modules_list) > run rhosts=<IP>
```

---
## References

### Hacktricks

- [Hacktricks: 873 - Pentesting Rsync](https://book.hacktricks.wiki/en/network-services-pentesting/873-pentesting-rsync.html)