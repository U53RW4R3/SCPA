# Fortinet

## Dorks

`fortinet`

## CLI Command

```
$ shodan download --limit 5000000 fortinet_vpn_appliances.json.gz fortinet

$ shodan parse fortinet_vpn_appliances.json.gz --fields=ip_str,port > fortinet_ips.txt
```