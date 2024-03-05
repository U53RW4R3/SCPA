# Base64

Search Tag(s): #command-line #use-cases #linux

## Powershell one-liner encoded

- Three different options to encode base64

```
$ str="a string"

$ echo -en $str | iconv -t UTF-16LE | base64 -w 0

$ echo -en $str | iconv -t UTF-16LE | openssl enc -base64 -A

$ echo -en $str | iconv -t UTF-16LE | openssl enc -a -e -A
```

- You can read it from a file

```
$ iconv -f ASCII -t UTF-16LE file.txt | base64 -w 0

$ iconv -f ASCII -t UTF-16LE file.txt | openssl enc -base64 -A

$ iconv -f ASCII -t UTF-16LE file.txt | openssl enc -a -e -A
```