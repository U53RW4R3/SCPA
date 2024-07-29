# NetExec

- Username and password

```
$ netexec winrm <IP> -u users.lst -p passwords.lst [-d <domain> | --local-auth]
```

- Username and NTLM hashes

```
$ netexec winrm <IP> -u users.lst -H hashes.lst [-d <domain> | --local-auth]
```