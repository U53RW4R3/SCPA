# SBD

## 01 - Reverse Shell Handler

```
$ sbd -lnvp <PORT>
```

Any listening ports ranging between **1-1023** must be ran as `root`.

```
$ sudo sbd -lnvp 80
```

## 02 - Bind Shell Handler

```
$ sbd -lnvp <target_IP> <target_PORT>
```

---
## References

- [Kali.org Tools: SBD](https://www.kali.org/tools/sbd/)