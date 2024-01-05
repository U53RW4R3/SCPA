# Metasploit

TODO: Fill this info

```
msf > use auxiliary/scanner/http/wordpress_scanner

msf auxiliary(wordpress_scanner) > options

msf auxiliary(wordpress_scanner) > set ssl <true | false>

msf auxiliary(wordpress_scanner) > set targeturi /path/to/uri

msf auxiliary(wordpress_scanner) > set rhosts <IP>

msf auxiliary(wordpress_scanner) > set rport <PORT>

msf auxiliary(wordpress_scanner) > run
```