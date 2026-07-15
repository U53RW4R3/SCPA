# Resource

## 01 - Save Commands

Save the initial commands that were executed to a file.

```
msf > makerc msf_commands.rc
```

## 02 - Execute Resource File

### 2.1 - Interactive Session

Insert multiple post modules and options for either a `meterpreter` or a regular `shell` session.

```
post/multi/recon/local_exploit_suggester
post/windows/gather/enum_shares
post/linux/gather/enum_configs PLATFORM=linux
post/multi/gather/env DOMAIN=corp.local
```

Then automated the post modules.

```
meterpreter > run post/multi/manage/multi_post macro=/path/to/session_commands.txt
```

### 2.2 - Meterpreter

Insert multiple `meterpreter` commands.

```
getuid
sysinfo
ifconfig
```

Then automate it.

```
meterpreter > run post/multi/gather/run_console_rc_file resource=/path/to/meterpreter_commands.rc
```

Insert multiple shell commands from a `meterpreter` session.

```rb
whoami
hostname
```

Then execute the commands in a file.

```
meterpreter > run post/multi/gather/multi_command resource=/path/to/shell_commands.txt
```

### 2.3 - Meta Shell

```
resource /path/to/local/resource_1.rc /path/to/local/resource_n.rc
```

## 03 - Debug Current Session

### 3.1 - Meterpreter

```
meterpreter > pry
```

### 3.2 - Meta Shell

```
pry
```

## 04 - Automate Metasploit Commands

Then run it with `msfconsole`.

```
$ sudo msfconsole -qr /path/to/resource.rc
```

---
## References

### Source Repositories

- [rapid7: metasploit framework resource scripts](https://github.com/rapid7/metasploit-framework/tree/master/scripts/resource)

- [r00t-3xp10it: Resource Files](https://github.com/r00t-3xp10it/resource_files)

- [r00t-3xp10it: metasploit_resource_files](https://github.com/r00t-3xp10it/hacking-material-books/blob/master/metasploit-RC%5BERB%5D/metasploit_resource_files.md)

- [r00t-3xp10it: msf-auxiliarys](https://github.com/r00t-3xp10it/msf-auxiliarys/wiki/Welcome-to-the-msf-auxiliarys-wiki!)

### RubyFu

- [RubyFu: API and Extensions](https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/meterpreter/api-and-extensions)

- [RubyFu: Meterpreter Scripting](https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/meterpreter/meterpreter-scripting)

- [RubyFu: Railgun API Extension](https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/meterpreter/railgun-api-extension)