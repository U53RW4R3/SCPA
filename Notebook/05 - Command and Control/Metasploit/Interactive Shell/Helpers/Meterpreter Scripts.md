# Metasploit Modules

TODO: Lateral movement such as WMI

https://securitycafe.ro/2015/04/06/writing-a-metasploit-post-exploitation-module/

https://github.com/darkoperator/Meterpreter-Scripts

## Railgun

```
meterpreter > irb
>> session.railgun.known_dll_names
```

Retrieve `kernel32` functions.

```
>> session.railgun.kernel32.functions
```

Retrieve `shell32` functions.

```
>> session.railgun.shell32.functions
```

Replace `function_name()` with the actual WinAPI method to invoke it.

```
>> client.railgun.shell32.function_name()
```

---
## References

- [Metasploit Unleashed: Custom Scripting](https://www.offsec.com/metasploit-unleashed/custom-scripting/)

- [Metasploit Unleashed: Useful Functions](https://www.offsec.com/metasploit-unleashed/functions/)

- [Malicious.link: Am I an Admin? Railgun Script](https://malicious.link/posts/2010/2010-09-13-am-i-an-admin-railgun-script/)

- [Mubix: stuff](https://github.com/mubix/stuff)

- [r00t-3xp10it: Metasploit API CheatSheet](https://github.com/r00t-3xp10it/hacking-material-books/blob/master/metasploit-RC%5BERB%5D/metasploit-API/my-API-Cheat-sheet.md)

- [RubyFu: API and Extensions](https://rubyfu.net/module-0x5-or-exploitation-kung-fu/metasploit/meterpreter/api-and-extensions)