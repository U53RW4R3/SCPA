# Email Format

Note: Go to **View Page Source** on any web browser of your choice and save it as html file then use the `grep` command to parse it.

`$ grep -Eo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" file.html | sort -u > emails.txt`

---
## References

- [Email Format](https://www.email-format.com)