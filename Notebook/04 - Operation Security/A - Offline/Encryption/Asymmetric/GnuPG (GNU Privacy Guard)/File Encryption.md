# File Encryption

Search Tag(s): #operation-security #asymmetric #gnupg

## 1.1 - Encrypt File

Specify cipher algorithm and compress the file.

```
$ gpg -e -c --cipher-algo <IDEA | 3DES | CAST5 | AES256 | TWOFISH | CAMELLIA256> [--compress-algo <Uncompressed | ZIP | ZLIB | BZIP2>] file.txt -o file.txt.gpg
```

## 1.2 - Decrypt File

```
$ gpg -d -c --cipher-algo <IDEA | 3DES | CAST5 | AES256 | TWOFISH | CAMELLIA256> file.txt.gpg -o file.txt
```

---
## References

### Backlinks

- [[Cryptography]]