# Nmap

`$ nmap -p 80,443 -Pn -n --script http-fileupload-exploiter --script-args http.useragent='<user_agent>' <IP>`