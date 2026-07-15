# LeakSearch

## 01 - Setup

```
$ sudo git clone https://github.com/JoelGMSec/LeakSearch /opt/intelligence-gathering/LeakSearch && \
sudo ln /opt/intelligence-gathering/LeakSearch/LeakSearch.py /usr/local/bin/leaksearch && \
sudo chmod 755 /usr/local/bin/leaksearch
```

## 02 - Help Menu

```
$ leaksearch -h

  _               _     ____                      _
 | |    ___  __ _| | __/ ___|  ___  __ _ _ __ ___| |__
 | |   / _ \/ _` | |/ /\___ \ / _ \/ _` | '__/ __| '_ \
 | |__|  __/ (_| |   <  ___) |  __/ (_| | | | (__| | | |
 |_____\___|\__,_|_|\_\|____/ \___|\__,_|_|  \___|_| |_|

  ------------------- by @JoelGMSec -------------------

usage: leaksearch [-h] [-d DATABASE] [-k KEYWORD] [-n NUMBER] [-o OUTPUT] [-p PROXY]

options:
  -h, --help            show this help message and exit
  -d DATABASE, --database DATABASE
                        Database used for the search (ProxyNova or LocalFile)
  -k KEYWORD, --keyword KEYWORD
                        Keyword (user/domain/pass) to search for leaks in the DB
  -n NUMBER, --number NUMBER
                        Number of results to show (default is 20)
  -o OUTPUT, --output OUTPUT
                        Save the results as json or txt into a file
  -p PROXY, --proxy PROXY
                        Set HTTP/S proxy (like http://localhost:8080)
```

## 03 - Usage

TODO: Fill this info

---
## References

- [LeakSearch](https://github.com/JoelGMSec/LeakSearch)

- [Darkbyte: Searching and leaking passwords with LeakSearch](https://darkbyte.net/buscando-y-filtrando-contrasenas-con-leaksearch/)