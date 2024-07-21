# Manual

Note: some websites I've discovered that they couldn't work with `curl` or `wget` in this case go to **View Page Source** on any web browser of your choice and save it as html file then use the `grep` command to parse it.

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

## Github Commits Checksum

In the web browser by checking the git commits. You can identify emails and timezones from the specific repository.

```
https://github.com/<username>/<git_repo>/commit/<commit_id>

https://github.com/<username>/<git_repo>/commit/<commit_id>.patch
```

### OPSEC Consideration

Note: They don't have to be real.

```
$ git config --global user.name "<username>"

$ git config --global user.email user@email.com
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/A - Information Gathering/04 - Forensics/DataSurgeon|DataSurgeon]]