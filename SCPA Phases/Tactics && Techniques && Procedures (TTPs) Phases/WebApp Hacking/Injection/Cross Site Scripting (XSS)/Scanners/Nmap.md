# Nmap

Search Tag(s): #nmap #information-gathering #active-reconnaissance #xss #webapp

## DOM-Based XSS

`$ nmap -p80,443 --script http-dombased-xss <IP>`

## Stored XSS

`$ nmap -p80,443 --script http-stored-xss <IP>`

## PHP Self XSS

`$ nmap -p80,443 --script http-phpself-xss <IP>`

## XSSed Database

`$ nmap -p80,443 --script http-xssed <IP>`