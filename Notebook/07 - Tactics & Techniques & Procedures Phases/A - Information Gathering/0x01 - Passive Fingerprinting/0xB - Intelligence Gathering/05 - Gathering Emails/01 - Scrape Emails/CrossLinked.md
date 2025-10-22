# [[03 - Offensive Infrastructure/E - Setup Machine/0x02 - Offensive Tools/Reconnaissance/OSINT/CrossLinked|CrossLinked]]

## Basic Format

```
$ crosslinked --proxy-file proxies.txt -f '{first}.{last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{f}.{last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{f}{last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{first}.{l}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '<DOMAIN>\{first}.{last}' -t 15 -j 30 "<organization_name>"
```

## Advanced Formatting

```
$ crosslinked --proxy-file proxies.txt -f '{0:first}.{-2:last}@domain.com' -t 15 -j 30 "<organization_name>"

$ crosslinked --proxy-file proxies.txt -f '{first}.{1:last}@domain.com' -t 15 -j 30 "<organization_name>"
```

---
## References

### Hackers Arise

- [Hackers Arise: Using QRCodes in Phishing and Social Media Attacks](https://hackers-arise.com/cyberwar-mission-3-turning-your-enemies-strength-against-them/)

- [Hackers Arise: Using QRCodes in Phishing and Social Media Attacks](https://hackers-arise.com/cyberwar-mission-3-turning-your-enemies-strength-against-them-2/)