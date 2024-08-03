# SBD

## 01 - Reverse shell

```
$ sbd -lnvp <PORT>
```

Any listening ports ranging between **1-1023** must be ran as `root`.

```
$ sudo sbd -lnvp 80
```

## 02 - Bind shell

```
$ sbd -lnvp <target_IP> <target_PORT>
```

---
## References

- [SBD: Usage](https://www.kali.org/tools/sbd/)