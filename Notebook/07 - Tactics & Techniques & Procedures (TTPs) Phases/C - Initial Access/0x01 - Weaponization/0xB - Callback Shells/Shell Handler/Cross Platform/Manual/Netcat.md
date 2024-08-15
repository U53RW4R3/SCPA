# Netcat

## 01 - Reverse Shell Handler

```
$ nc -lnvp <PORT>
```

Any listening ports ranging between **1-1023** must be ran as `root`.

```
$ sudo nc -lnvp 80
```

## 02 - Bind Shell Handler

```
$ nc -lnvp <target_IP> <target_PORT>
```