# 04 - Text Manipulation

## 4.2 - Sed

Remove empty lines.

```
$ sed -i "/^$/d" file.txt
```

## 4.3 - ANSIFilter

Remove ANSI characters.

```
$ sudo apt install -y ansifilter

$ ansifilter -i file.txt -o striped_ansi.txt
```

---
## References

- [Grep Multiple Strings](https://phoenixnap.com/kb/grep-multiple-strings)