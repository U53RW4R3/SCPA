# Scrape URLs

```
$ curl -s http[s]://<IP> | grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" | cut -d "/" -f 3 | sort -u > urls.txt"

$ curl -s http[s]://<IP> | grep "title\|href" | sed -e 's/^[[:space::]]*//'

$ wget -qO- http[s]://<IP> | grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" | cut -d "/" -f 3 | sort -u > urls.txt"

$ wget -qO- http[s]://<IP> | grep "title\|href" | sed -e 's/^[[:space::]]*//'
```

> [!NOTE]
> Some websites I've discovered that they couldn't work with `curl` or `wget` by requesting an HTTP to read the contents. Another way is to save the webpage contents (**Right Click -> Save Page As...**) on any web browser of your choice and save it as `.html` file then use the `grep` command to parse it.

```
$ grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" file.html | awk -F "/" '{print $3}' | sort -u > urls.txt

$ grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" file.html | cut -d "/" -f 3 | sort -u > urls.txt"

$ grep "title\|href" file.html | sed -e 's/^[[:space::]]*//'
```

For extracting HTTPS, FTP and other URL format use

```
$ grep -E '(((https|ftp|gopher)|mailto)[.:][^ >"	]*|www.[-a-z0-9.]+)[^ .,;	>">):]' file.html > urls.txt
```

Scrape javascript files of URLs.

```
$ curl -s http[s]://<IP>/file.js | grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" | cut -d "/" -f 3 | sort -u > urls.txt

$ curl -s http[s]://<IP>/file.js | grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" | awk -F "/" '{print $3}' | sort -u > urls.txt

$ wget -qO- http[s]://<IP>/file.js | grep -Eo "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?" | cut -d "/" -f 3 | sort -u > urls.txt"
```

## DataSurgeon

```
$ curl -s http[s]://<IP> | ds -uC | uniq

$ wget -qO- http[s]://<IP> | ds -uC | uniq
```

---
## References

### Backlinks

- [[DataSurgeon|DataSurgeon]]

### Hacktricks

- [Hacktricks: Useful Linux Commands](https://book.hacktricks.wiki/en/linux-hardening/useful-linux-commands.html)

### Websites

#### Aware Online

- [Aware Online: Website search tool](https://www.aware-online.com/en/osint-tools/website-search-tool/)

- [Aware Online: Website tools](https://www.aware-online.com/en/osint-tools/website-tools/)

#### Encyclopedia

- [Wikipedia](https://www.wikipedia.org)

#### List of companies

- [Powrbot](https://powrbot.com)