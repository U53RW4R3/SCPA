# Nmap

`$ nmap -p 445 --script "safe or smb-enum-*" <IP>`

TODO: Re-arrange from this section to post exploitation

`$ nmap -p 445 --script smb-os-discovery --script-args unsafe=1 <IP>`

`$ nmap -p 445 --script smb-security-mode <IP>`

`$ nmap -p 445 --script smb2-security-mode,smb2-capabilities.nse <IP>`

`$ nmap -p 445 --script smb-server-stats <IP>`

`$ nmap -p 445 --script smb-system-info <IP>`

`$ nmap -p 445 --script smb-protocols <IP>`