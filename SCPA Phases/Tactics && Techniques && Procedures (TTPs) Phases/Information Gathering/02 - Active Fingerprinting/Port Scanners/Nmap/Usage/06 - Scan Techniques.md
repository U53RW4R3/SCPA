# 06 - Scan Techniques

## 6.1 - TCP

- TCP Connect Scan

`$ sudo nmap -sT <IP>`

- Syn "Half-open" Scan (Stealth Mode)

`$ sudo nmap -sS <IP>`

## 6.2 - UDP

- UDP Scan

`$ sudo nmap -sU <IP>`

## 6.3 - Other Scan Types

- TCP Null Scan

`$ sudo nmap -sN <IP>`

- FIN Scan

`$ sudo nmap -sF <IP>`

- Xmas Scan

`$ sudo nmap -sX <IP>`

- ACK Scan

`$ sudo nmap -sA <IP>`

- Window Scan

`$ sudo nmap -sW <IP>`

- Maimon Scan

`$ sudo nmap -sM <IP>`

## 6.4 - Version Detection

- Detect operating system

`$ sudo nmap -O <IP>`

- Service Version detection ^07168f

`$ sudo nmap -sV <IP>`

`$ sudo nmap -sV --version-all <IP>`

---
## References

- [Nmap usage tips](https://miloserdov.org/?p=3639)