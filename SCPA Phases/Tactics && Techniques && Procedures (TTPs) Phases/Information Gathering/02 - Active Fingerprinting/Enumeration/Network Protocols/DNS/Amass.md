ssh# Amass

```
$ amass enum -brute -d <website.com> -w subdomains-wordlists.txt -o subdomains.txt

$ amass enum -active -df domains.txt -w subdomains-wordlists.txt -o subdomains.txt

$ amass db -df domains.txt -names -o subdomains.txt
```

---
## References

- [Amass Tutorial](https://github.com/OWASP/Amass/wiki/Tutorial)

- [Amass User Guide](https://github.com/OWASP/Amass/wiki/User-Guide)

- [Amass Quick Tutorial Example Usage](https://allabouttesting.org/owasp-amass-quick-tutorial-example-usage/)