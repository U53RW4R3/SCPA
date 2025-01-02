# Manual

> [!NOTE]
> ome websites I've discovered that they couldn't work with `curl` or `wget` in this case go to **View Page Source** on any web browser of your choice and save it as html file then use the `grep` command to parse it.

```
$ wget -qO- http[s]://<IP> | grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" | sort -u > emails.txt

$ curl -s http[s]://<IP> | grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" | sort -u > emails.txt

$ grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" file.html | sort -u > emails.txt
```

## DataSurgeon

```
$ curl -s http[s]://<IP> | ds -eC | uniq

$ wget -qO- http[s]://<IP> | ds -eC | uniq
```

---
## References

### Backlinks

- [[DataSurgeon|DataSurgeon]]

### Websites

- [Aware Online: E-mail Search Tool](https://www.aware-online.com/osint-tools/e-mail-search-tool/)

- [Aware Online: Email Address Tool](https://www.aware-online.com/en/osint-tools/email-address-tools/)