# Nmap

`$ nmap -p 443 -Pn --script ssl-date,ssl-cert-intaddr,ssl-enum-ciphers,sslv2 <IP>`

- Probe for subdomains

`$ nmap -p 443 -Pn --script ssl-cert <IP>`