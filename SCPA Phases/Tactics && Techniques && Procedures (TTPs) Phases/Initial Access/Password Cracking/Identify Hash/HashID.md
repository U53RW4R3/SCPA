# HashID

^0f21a0

## 01 - Help Menu

```
$ hashid -h
usage: hashid.py [-h] [-e] [-m] [-j] [-o FILE] [--version] INPUT

Identify the different types of hashes used to encrypt data

positional arguments:
  INPUT                    input to analyze (default: STDIN)

options:
  -e, --extended           list all possible hash algorithms including salted passwords
  -m, --mode               show corresponding Hashcat mode in output
  -j, --john               show corresponding JohnTheRipper format in output
  -o FILE, --outfile FILE  write output to file
  -h, --help               show this help message and exit
  --version                show program's version number and exit

License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
```

## 02 - Usage

`$ hashid <hash>`