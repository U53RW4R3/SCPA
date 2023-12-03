# 02 - Port Specification and Scan Order

- Specify port to scan

`$ sudo nmap -p <PORT>`

- Port range to scan

`$ sudo nmap -p 21-23 <IP>`

- Port list to scan

`$ sudo nmap -p 25,53,80,443`

- Port range and list to scan

`$ sudo nmap -p 21-23,25,53,80 <IP>`

- Scan all ports

`$ sudo nmap -p- <IP>`

- Show open ports

`$ sudo nmap --open <IP>`

---
## References

- [Nmap usage tips](https://miloserdov.org/?p=3639)