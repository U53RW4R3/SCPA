# Sliver

Search Tag(s): #red-team-infrastructure #sliver #detection

## 01 - Shodan

`ssl:multiplayer ssl:operators`

## 02 - JARM

`$ git clone https://github.com/salesforce/jarm.git`

`$ cd jarm/`

`$ python jarm.py <C2_IP> -p 8888`

`$ python jarm.py <C2_IP> -p 443`

`$ python jarm.py <C2_IP> -p 80`

---
## References

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)

- [JARM](https://github.com/salesforce/jarm)

- [Detecting Sliver C2 framework with Wazuh](https://wazuh.com/blog/detecting-sliver-c2-framework-with-wazuh/)