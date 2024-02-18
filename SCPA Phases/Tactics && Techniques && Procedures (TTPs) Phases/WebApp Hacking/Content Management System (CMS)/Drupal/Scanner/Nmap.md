# Nmap

`$ nmap -p 80,443 --script http-drupal-enum --script-args http.useragent='<user_agent>' <IP>`

- Enumerate user accounts in Drupal 

`$ nmap -p 80,443 --script http-drupal-enum-users --script-args http.useragent='<user_agent>' <IP>`

---
## References

- [[User Agents]]