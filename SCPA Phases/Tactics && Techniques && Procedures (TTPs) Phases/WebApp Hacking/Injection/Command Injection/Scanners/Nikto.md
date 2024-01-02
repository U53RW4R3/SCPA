# Nikto

- Check for command injection known exploits.

`$ nikto -host <IP> -T 8 -no404`

- Bruteforce common CGI directories.

`$ nikto -host <IP> -Cgidirs all -no404`

- Enumerate possible CGI directories.

`$ nikto -host <IP> -Plugins:cgi -no404`

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/Vulnerability Assessment/Web Vulnerability Scanner/Nikto|Nikto]]