# Description

## Bruteforce

```
$ hydra -L users.lst -P passwords.lst http-get <IP> [-s <PORT>]

$ hydra -L users.lst -P passwords.lst http-get://<IP>:[<PORT>][/path/to/URI]
```