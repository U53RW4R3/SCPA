# Base64

Search Tag(s): #command-line #use-cases #linux

## Powershell one-liner encoded

Three different options to encode base64.

```
$ str="a string"

$ echo -en $str | iconv -t UTF-16LE | base64 -w 0

$ echo -en $str | iconv -t UTF-16LE | basenc -w 0 --base64

$ echo -en $str | iconv -t UTF-16LE | openssl enc -base64 -A

$ echo -en $str | iconv -t UTF-16LE | openssl enc -a -e -A
```