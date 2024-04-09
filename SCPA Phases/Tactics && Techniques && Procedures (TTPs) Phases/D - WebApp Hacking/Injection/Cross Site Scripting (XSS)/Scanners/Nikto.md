# Nikto

Search Tag(s): #information-gathering #active-reconnaissance #xss #webapp

- Check for XSS known exploits.

```
$ nikto -h <IP> -Plugins apache_expect_xss -no404

$ nikto -h <IP> -T 4 -no404
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/C - Vulnerability Assessment/Web Vulnerability Scanner/Nikto|Nikto]]