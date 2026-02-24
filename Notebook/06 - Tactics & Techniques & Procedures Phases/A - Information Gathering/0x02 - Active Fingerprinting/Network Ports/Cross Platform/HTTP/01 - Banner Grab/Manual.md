# Manual

## 01 - Table Reference

| IIS Version | Windows Operating System Version |
| ----------- | -------------------------------- |
| 1.0         | NT Server 3.51                   |
| 2.0         | NT Server 4.0                    |
| 3.0         | NT Server 4.0                    |
| 4.0         | NT Server 4.0 SP 3               |
| 5.0         | Windows 2000                     |
| 5.1         | Windows XP Professional          |
| 6.0         | Windows Server 2003              |
| 7.0         | Windows Vista and Server 2008    |
| 7.5         | Windows 7 and 2008 R2            |
| 8.0         | Windows 8 and Server 2012        |

## 02 - Ncat

```
$ echo "EXIT" | ncat <IP> 80

$ printf "GET / HTTP/1.0\r\n\r\n" | ncat <IP> 80

$ printf "HEAD / HTTP/1.0\r\n\r\n" | ncat <IP> 80

$ echo "" | ncat -v <IP> 80
```

If it has a secure certificate that you see a protocol of HTTPS with a letter (s) add a flag `--ssl`.

```
$ printf "GET / HTTP/1.0\r\n\r\n" | ncat <IP> 443 --ssl
```

## 03 - cURL

```
$ curl -s -A "<user_agent>" -s -I <IP> | grep -e "Server: "
```

## 04 - Wget

```
$ wget -U "<user_agent>" -q -S <IP>
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/D - Webapp Pentesting/0x03 - Bypass Webapp Security/Web Application Firewall (WAF)/Helpers/User Agents|Webapp Pentesting: User Agents]]