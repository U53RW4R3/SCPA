# CheckPoint Firewall

## 01 - Manual

```
$ echo -ne '\x51\x00\x00\x00\x00\x00\x00\x21\x00\x00\x00\x0bsecuremote\x00' | nc -q 1 <target_IP> 264 | grep -a CN | cut -c 2-

$ printf '\x51\x00\x00\x00\x00\x00\x00\x21\x00\x00\x00\x0bsecuremote\x00' | nc -q 1 <target_IP> 264 | grep -a CN | cut -c 2-
```

## 02 - Metasploit

```
msf > use auxiliary/gather/checkpoint_hostname

msf auxiliary(gather/checkpoint_hostname) > set rhosts <target_IP>
```

---
## References

### Hacktricks

- [Hacktricks: 264 - Pentesting Check Point FireWall-1](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-264-check-point-firewall-1.html)