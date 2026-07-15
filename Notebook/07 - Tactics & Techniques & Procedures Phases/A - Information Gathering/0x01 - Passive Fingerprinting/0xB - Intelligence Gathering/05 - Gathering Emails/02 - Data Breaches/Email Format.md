# Email Format

> [!NOTE] Parse Webpage's HTML Source
> Go to **View Page Source** on any web browser of your choice and save it as html file then use the `grep` command to parse it.

```
$ grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" file.html | sort -uo emails.txt
```

---
## References

### Email Format

- [Email Format](https://www.email-format.com)