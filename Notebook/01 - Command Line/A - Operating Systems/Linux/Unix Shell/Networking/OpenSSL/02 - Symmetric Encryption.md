---
author(s):
  - Userware
tags:
  - command-line
  - cryptography
  - linux
---
# 02 - Symmetric Encryption

## 2.1 - List Cipher Names

```
$ openssl enc -list
```

## 2.2 - Encryption

Without salt (`-nosalt`).
  
```  
$ openssl <cipher_name> [-a] -nosalt -in file.txt -out file.txt.enc
```

With salt (`-salt`).

```
$ openssl <cipher_name> [-a] -salt -in file.txt -out file.txt.enc
```  
  
## 2.3 - Decryption
  
```  
$ openssl <cipher_name> [-a] -d -in file.txt.enc -out file.txt 
```