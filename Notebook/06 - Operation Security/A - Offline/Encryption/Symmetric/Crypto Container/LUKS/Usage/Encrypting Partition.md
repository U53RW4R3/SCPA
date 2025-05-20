# Encrypting Partition

Search Tag(s): #help-menu #operation-security #cryptography #luks #command-line #linux

- List available encryption methods. The format parsed by the kernel is `"cipher[:keycount]-mode-ivmode[:ivopts]"`. Examples: `aes-xts-plain64, blowfish-cbc-essiv:sha256, aes:64-cbc-lmk`.

```
$ cryptsetup benchmark

$ echo "#     Algorithm |       Key |      Encryption |      Decryption";for i in $ciphers ; do cryptsetup benchmark --cipher $i|tail -n 1; done
```

```
$ cryptsetup --type luks2 -c aes-xts-plain64 -h sha512 -s 512 --pbkdf argon2id --use-urandom -y [--label <label_name>] luksFormat /path/to/container_or_drive
```

- List block devices

```
$ lsblk
```

---
## References

- [Kali Docs: Raspberry Pi - Full Disk Encryption](https://www.kali.org/docs/arm/raspberry-pi-with-luks-full-disk-encryption-2/)

- [Kali RPI LUKS Crypt](https://github.com/tothi/kali-rpi-luks-crypt)

- [OffSec: Kali Linux on a Raspberry Pi (A/B+/2) with Disk Encryption](https://www.offsec.com/kali-linux/raspberry-pi-luks-disk-encryption/)