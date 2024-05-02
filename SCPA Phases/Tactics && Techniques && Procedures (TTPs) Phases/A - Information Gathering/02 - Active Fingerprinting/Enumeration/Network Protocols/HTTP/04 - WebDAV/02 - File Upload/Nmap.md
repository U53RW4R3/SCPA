# Nmap

`$ nmap -p 80,443 -Pn -n --script http-put --script-args http-put.url='<upload_directory>',http-put.file='<file>' <IP>`