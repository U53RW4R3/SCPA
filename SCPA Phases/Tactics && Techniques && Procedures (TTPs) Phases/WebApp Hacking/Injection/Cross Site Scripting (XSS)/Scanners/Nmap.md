# Nmap

Search Tag(s): #nmap #information-gathering #active-reconnaissance #xss #webapp

## DOM-Based XSS

`$ nmap -p80,443 -Pn -n --script http-dombased-xss --script-args http.useragent='<user_agent>' <IP>`

## Stored XSS

`$ nmap -p80,443 -Pn -n --script http-stored-xss --script-args http.useragent='<user_agent>' <IP>`

## PHP Self XSS

`$ nmap -p80,443 -Pn -n --script http-phpself-xss --script-args http.useragent='<user_agent>' <IP>`

## XSSed Database

`$ nmap -p80,443 -Pn -n --script http-xssed --script-args http.useragent='<user_agent>' <IP>`