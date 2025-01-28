---
author(s):
  - Userware
tags:
  - command-line
  - linux
---
# 03 - View Files

## 3.1 - View File Contents

Concatenate the file using `cat`.

```
$ cat file.txt
```

Concatenate the file in reverse using `tac` which is `cat` command in reverse.

```
$ tac file.txt
```

## 3.2 - View Page Content

View the file while navigating.

```
$ less file.txt
```

Read file with raw characters including color coded ANSI characters.

```
$ less -r file.txt
```

Similar to `less` but has a feature after viewing the contents when reaching the end of the line. You can scroll up to see the contents.

```
$ more file.txt
```

## 3.3 - View Partial File Contents

Specify the number of lines from the start of the file.

```
$ head -n 10 file.txt
```

Specify the number of lines from the end of the file.

```
$ tail -n 10 file.txt
```

## 3.4 - Wrap File Output

```
$ fold -w 25 file.txt
```

## 3.5 - Print Newline, Word and Byte counts

Display number of lines in a file.

```
$ wc -l file.txt
```

Display number of words in a file.

```
$ wc -w file.txt
```

Display number of characters in a file.

```
$ wc -m file.txt
```

Display number of bytes in a file.

```
$ wc -c file.txt
```