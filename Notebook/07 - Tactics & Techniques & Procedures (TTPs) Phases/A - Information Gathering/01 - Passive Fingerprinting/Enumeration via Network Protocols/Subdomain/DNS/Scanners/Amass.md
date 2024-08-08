# Amass

## 01 - Basics

```
$ amass enum -passive -d <domain.com> [-trqps 15] -dir recon_output

$ amass enum -passive -df domains.txt [-trqps 15] -dir recon_output

$ amass enum -passive -df domains.txt [-trqps 15] -o subdomains.txt && awk '{ system("resolveip -s "$1)}' subdomains.txt > ip_targets.txt
```

Track new changes when performing another recon.

```
$ amass track -dir recon_output -d <domain.com>
```

Output the results stored in a directory.

```
$ amass db -df domains.txt -names -o subdomains.txt

$ amass db -dir recon_output -names -o subdomains.txt
```

## 02 - Reverse DNS

```
$ amass intel -ip -cidr <IP>/<CIDR>
```

---
## References

- [Amass Tutorial](https://github.com/OWASP/Amass/wiki/Tutorial)

- [Amass User Guide](https://github.com/OWASP/Amass/wiki/User-Guide)

- [Amass Quick Tutorial Example Usage](https://allabouttesting.org/owasp-amass-quick-tutorial-example-usage/)