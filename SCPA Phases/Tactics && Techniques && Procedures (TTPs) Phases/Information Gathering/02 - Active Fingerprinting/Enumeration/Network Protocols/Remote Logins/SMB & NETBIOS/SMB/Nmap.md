# Nmap

`$ nmap -p 445 -Pn --script "safe or smb-enum-*" <IP>`

TODO: Re-arrange from this section to post exploitation

`$ nmap -p 445 -Pn --script smb-vuln-* --script-args unsafe=1 <IP>`

`$ nmap -p 445 -Pn --script smb-os-discovery --script-args unsafe=1 <IP>`

`$ nmap -p 445 -Pn --script smb-security-mode <IP>`

`$ nmap -p 445 -Pn --script smb2-security-mode,smb2-capabilities.nse <IP>`

`$ nmap -p 445 -Pn --script smb-server-stats <IP>`

`$ nmap -p 445 -Pn --script smb-system-info <IP>`

`$ nmap -p 445 -Pn --script smb-protocols <IP>`