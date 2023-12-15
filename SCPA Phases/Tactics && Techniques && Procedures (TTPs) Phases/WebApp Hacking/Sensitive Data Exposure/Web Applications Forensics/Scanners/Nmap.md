# Nmap

- Find HTML and JavaScript comments to find sensitive data.

`$ nmap -p80,443 --script http-comments-displayer <IP>`

- Find exposed git config repositories.

`$ nmap -p 80,443,8080 -Pn -n -sV --script http-git <IP>`

- Extract metadata

`$ nmap -p 80,443 -Pn -n --script http-exif-spider <IP>`