# Manual

**Note:** some websites I've discovered that they couldn't work with `curl` or `wget` in this case go to **View Page Source** on any web browser of your choice and save it as html file then use the `grep` command to parse it.

```
$ wget -qO- http[s]://<IP> | grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" | sort -u > emails.txt

$ curl -s http[s]://<IP> | grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" | sort -u > emails.txt

$ grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" file.html | sort -u > emails.txt
```