# Manual

## 01 - Ncat

```
$ echo "EXIT" | ncat <IP> 80

$ printf "GET / HTTP/1.0\r\n\r\n" | ncat <IP> 80

$ printf "HEAD / HTTP/1.0\r\n\r\n" | ncat <IP> 80

$ echo "" | ncat -v <IP> 80
```

* If it has a secure certificate that you see a protocol of HTTPS with a letter (s) add a flag `--ssl`

`$ printf "GET / HTTP/1.0\r\n\r\n" | ncat <IP> 443 --ssl`

## 02 - cURL

`$ curl -s -A "<user_agent>" -s -I <IP> | grep -e "Server: "`

## 03 - Wget

`$ wget -U "<user_agent>" <IP> -q -S`

---
## References

- [[User Agents]]