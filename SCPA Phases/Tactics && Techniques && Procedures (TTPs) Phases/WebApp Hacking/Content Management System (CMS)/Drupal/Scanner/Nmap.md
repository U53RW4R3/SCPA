# Nmap

`$ nmap -p 80,443 --script http-drupal-enum --script-args http.useragent='<user_agent>' <IP>`

`$ nmap -p 80,443 --script http-drupal-enum-users --script-args http.useragent='<user_agent>' <IP>`