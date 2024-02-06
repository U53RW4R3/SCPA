# JTR

## 01 - Usage

- List formats

`$ john --list=formats`

- Specify format to crack the hash

`$ john --format=<format> --wordlist=passwords.lst hashes.txt`

- Using standard rules by cracking the has that JTR comes with

`$ john --rules --format=<format> --wordlist=passwords.lst hashes.txt`

## 02 - Hashes

### 2.1 - General

#### 2.1.1 - MD5

`$ john --format=Raw-MD5 --wordlist=passwords.lst md5hashes.txt`

#### 2.1.2 - Zip

`$ zip2john file.zip > hash_zip.txt`

`$ john --format=zip --wordlist=passwords.lst hash_zip.txt`

### 2.2 - Linux

TODO: Provide more use cases of cracking hashes in Linux

### 2.3 - Windows

#### 2.3.1 - NTLM

`$ john --format=NT --wordlist=passwords.lst ntlm-hashes.txt`

#### 2.3.2 - NTLMv2-SSP

- When using Responder to perform MITM to fetch NTLMv2-SSP hashes via LLMNR/NBT-NS/mDNS poisoning

`$ john --format=netntlmv2 --wordlist=passwords.lst netntlmv2-hashes.txt`

#### 2.3.3 - Kerberoasting

^0c9a3c

`$ john --format=krb5tgs --wordlist=passwords.lst krbtgt-hashes.txt`

#### 2.3.4 - ASREPRoast

^0c9a3c

`$ john --format=krb5asrep --wordlist=passwords.lst asreptgt-hashes.txt`

---
## References

- [Kali Hashcat and John the Ripper Crack Windows Password Hashdump](https://pentesthacker.wordpress.com/2020/12/27/kali-hashcat-and-john-the-ripper-crack-windows-password-hashdump/)

- [Comprehensive Guide to John the Ripper. Part 1: Introducing and Installing John the Ripper](https://miloserdov.org/?p=4961&PageSpeed=noscript)

- [NotSoSecure: One Rule to Rule Them All](https://notsosecure.com/one-rule-to-rule-them-all)

- [NotSoSecure: Password Cracking Rules](https://github.com/NotSoSecure/password_cracking_rules)

- [Custom Rules for John The Ripper](https://web.archive.org/web/20200813234129/https://gracefulsecurity.com/custom-rules-for-john-the-ripper/)

- [Custom Rules for John The Ripper Examples](https://web.archive.org/web/20200814150401/https://gracefulsecurity.com/custom-rules-for-john-the-ripper-examples/)

- [Hackers Arise: Password Cracking Strategy](https://www.hackers-arise.com/password-cracking-strategy)