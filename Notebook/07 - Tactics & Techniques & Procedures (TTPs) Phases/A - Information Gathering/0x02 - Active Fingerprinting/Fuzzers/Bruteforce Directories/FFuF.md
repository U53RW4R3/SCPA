# FFuF

## 01 - Setup

```
$ go install github.com/ffuf/ffuf/v2@latest && \
sudo mv ~/go/bin/ffuf /usr/local/bin/
```

## 02 - Help Menu

```
$ ffuf -h
```

## 03 - Usage

```
$ ffuf -u http[s]://<IP>/FUZZ -w wordlist.txt -t 5
```

---
## References

- [FFuF](https://github.com/ffuf/ffuf)