# Manual

## 01 - Banner Grab

`$ nc -nv <IP> 79`

`$ echo "root" | nv -nv <IP> 79`

## 02 - User Enumeration

`$ finger @<IP>`

`$ finger <username>@<IP>`

`$ finger-user-enum.pl -U users.txt -t <IP>`

`$ finger-user-enum.pl -u <username> -t <IP>`

`$ finger-user-enum.pl -U users.txt -T ip_targets.txt`

---
## References

- [Hacktricks: Pentesting Finger](https://book.hacktricks.xyz/pentesting/pentesting-finger)

- [PentestMonkey: Finger-User-Enum](https://pentestmonkey.net/tools/user-enumeration/finger-user-enum)