# Uro

## 01 - Setup

```
$ git clone https://github.com/s0md3v/uro && cd uro && \
sudo python3 setup.py install
```

## 02 - Usage

`$ uro -i urls.txt -o truncated-output.txt`

## 03 - Use Cases

### Truncate Endpoints

`$ waybackurls <domain.com> | uro -o fuzz-endpoints-output.txt`

---
## References

- [Uro](https://github.com/s0md3v/uro)