# Description

## Bruteforce

```
$ hydra -L users.txt -P passwords.txt http-get <IP> [-s <PORT>]

$ hydra -L users.txt -P passwords.txt http-get://<IP>:[<PORT>][/path/to/URI]
```