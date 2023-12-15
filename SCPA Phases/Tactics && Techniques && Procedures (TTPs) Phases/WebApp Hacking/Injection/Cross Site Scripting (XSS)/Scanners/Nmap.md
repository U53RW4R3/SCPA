# Nmap

Search Tag(s): #nmap #information-gathering #active-reconnaissance #xss #webapp

## DOM-Based XSS

`$ nmap -p80,443 -Pn -n --script http-dombased-xss <IP>`

## Stored XSS

`$ nmap -p80,443 -Pn -n --script http-stored-xss <IP>`

## PHP Self XSS

`$ nmap -p80,443 -Pn -n --script http-phpself-xss <IP>`

## XSSed Database

`$ nmap -p80,443 -Pn -n --script http-xssed <IP>`