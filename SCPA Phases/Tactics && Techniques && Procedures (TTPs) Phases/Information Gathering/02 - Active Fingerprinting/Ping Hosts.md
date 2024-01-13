# Ping Hosts

`$ for i in $(cat ip_targets.txt); do ping -c 1 $i | grep -v "Name or service not known" | grep "64 bytes" | grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}"; done | tee active_ip_targets.txt`