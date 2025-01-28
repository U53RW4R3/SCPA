---
author(s):
  - Userware
tags:
  - command-line
  - use-cases
  - linux
---
# Alternative Concatenation Commands

First we'll take the number of lines.

```
$ filename=file.txt
lines=$(wc -l < $filename)
```

Then we'll use either `head` or `tail` to concatenate the file to view from the same file.

```
$ head -n $lines $filename

$ tail -n $lines $filename
```

---
## References

- [[03 - View Files|Linux: View Files]]