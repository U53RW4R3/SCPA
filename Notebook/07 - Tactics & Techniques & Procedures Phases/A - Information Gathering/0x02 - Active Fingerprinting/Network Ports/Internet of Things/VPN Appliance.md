# VPN Appliance

## Citrix

```
citrix-brute-xml.nse
citrix-enum-apps.nse
citrix-enum-apps-xml.nse
citrix-enum-servers.nse
citrix-enum-servers-xml.nse
```

## Cisco

```
$ nmap -p 443 -Pn -n --script http-cisco-anyconnect --script-args http.useragent='<user_agent>' <IP>
```