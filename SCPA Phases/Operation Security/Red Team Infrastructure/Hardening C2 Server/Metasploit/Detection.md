# Detection

Search Tag(s): #red-team-infrastructure #metasploit #detection

## 01 - Shodan

`ssl:"MetasploitSelfSignedCA"`

## 02 - JARM

`$ git clone https://github.com/salesforce/jarm.git`

`$ cd jarm/`

`$ python jarm.py <C2_IP> -p 4444`

`$ python jarm.py <C2_IP> -p 443`

`$ python jarm.py <C2_IP> -p 80`

---
## References

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)

- [JARM](https://github.com/salesforce/jarm)