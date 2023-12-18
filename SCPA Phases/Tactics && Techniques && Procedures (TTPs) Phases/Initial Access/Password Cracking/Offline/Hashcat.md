# Hashcat

## 01 - Usage

- Wordlist Attack-Mode

`$ hashcat -a 0 -m 0 md5hashes.txt passwords.lst`

- Brute-Force Attack-Mode

`$ hashcat -a 3 -m 0 md5hashes.txt ?a?a?a?a?a?a`

- Display the cracked hashes

`$ hashcat --show`

## 02 - Troubleshooting

### 2.1 - Arch-based distros

- These are the required dependencies that is from the AUR

`$ sudo pamac install opencl-amd hashcat-git`

- Always add the flag in order to use hashcat

`$ hashcat --self-test-disable`

## 03 - Hashes

TODO: Provide more examples of hashes

### 3.1 - General

#### 3.1.1 - MD5

`$ hashcat -m 0 -a 0 md5_hashes.txt passwords.lst`

### 3.2 - Wi-Fi

#### 3.2.1 - WPA-EAPOL-PBKDF2

`$ hashcat -m 2500 -a 0 wifi-handshakes.hccapx passwords.lst`

### 3.3 - Linux

TODO: Fill in this information related to cracking linux hashes

### 3.4 - Windows

#### 3.4.1 - LM

`$ hashcat -m 3000`

#### 3.4.2 - NTLM

`$ hashcat -m 1000`

#### 3.4.3 - Kerberoast

^87baa5

- **Kerberos 5, etype 23, TGS-REP**

`$ hashcat -m 13100`

#### 3.4.4 - ASREPRoast

^6d0af5

- **Kerberos 5, etype 23, AS-REP**

`$ hashcat -m 18200`

---
## References

- [Hashcat Example Hashes](https://hashcat.net/wiki/doku.php?id=example_hashes)

- [Better Hacking Through Cracking Know Your Rules](https://www.trustedsec.com/blog/better-hacking-through-cracking-know-your-rules/)

- [Hackers Arise: Password Cracking Strategy](https://www.hackers-arise.com/password-cracking-strategy)