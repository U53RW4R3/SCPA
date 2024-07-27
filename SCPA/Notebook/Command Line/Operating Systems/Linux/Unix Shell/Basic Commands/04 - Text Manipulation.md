# 04 - Text Manipulation

## 4.1 - Sed

Remove empty lines.

```
$ sed -i "/^$/d" file.txt

$ sed -i 's/ //g'

$ sed -i '/^[[:space:]]*$/d'
```

Remove all indentation.

```
$ sed 's/^[[:space:]]*//g'
```

## 4.2 - ANSIFilter

Remove ANSI characters.

```
$ sudo apt install -y ansifilter

$ ansifilter -i file.txt -o striped_ansi.txt
```

---
## References

- [Grep Multiple Strings](https://phoenixnap.com/kb/grep-multiple-strings)