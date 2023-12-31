# Nmap

TODO: Fill in this information

`$ nmap -p 80,443 --script http-brute --script-args http.useragent='<user_agent>' <IP>`

`$ nmap --script http-proxy-brute --script-args http.useragent='<user_agent>' <IP>`

`$ nmap --script http-form-brute --script-args http.useragent='<user_agent>' <IP>`

`$ nmap --script http-frontpage-login --script-args http.useragent='<user_agent>' <IP>`