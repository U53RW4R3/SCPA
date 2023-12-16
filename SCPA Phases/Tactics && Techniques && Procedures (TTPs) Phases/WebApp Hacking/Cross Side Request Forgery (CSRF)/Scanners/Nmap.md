# Nmap

```
$ nmap -p 80,443 -Pn -n --script http-cross-domain-policy <IP>

$ nmap -p 80,443 -Pn -n --script http-cross-domain-policy --script-args http-cross-domain-policy.domain-lookup=true <IP>
```

`$ nmap -p 80,443 -Pn -n --script http-csrf <IP>`