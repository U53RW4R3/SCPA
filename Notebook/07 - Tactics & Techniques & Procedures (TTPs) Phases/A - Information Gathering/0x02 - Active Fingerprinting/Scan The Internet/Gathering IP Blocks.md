# Gathering IP Blocks

## 01 - All IPs of a country

TODO: Fill this info

```
$ wget $(curl -s https://db-ip.com/db/download/city | grep -Eo 'https://download.db-ip.com/free/dbip-city-20[0-9]{2}-[0-9]{2}.csv.gz') && gunzip dbip-city-*.csv.gz && mv dbip-city-* dbip-city-csv
```

## 02 - All ISP IP Ranges

TODO: Fill this info

```
$ curl -s -L --data "<website.com>" https://2ip.me/en/services/information-service/provider-ip?a=act | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}/[0-9]{1,2}"
```

https://github.com/ip2location/ip2location-python-csv-converter

---
## References

### Ethical hacking and penetration testing

- [Ethical hacking and penetration testing: IP addresses databases of organizations and geographical places (continents, countries, provinces and cities)](https://miloserdov.org/?p=4156)

- [Ethical hacking and penetration testing: How to collect Location, Country or ISP IP Ranges](https://miloserdov.org/?p=17)

### Lookup IP Blocks

- [w-e-b.site](https://w-e-b.site/)

- [suIP.biz](https://suip.biz/)

- [DBIP](https://db-ip.com/)

- [2IP](https://2ip.me/en/)

- [IPInfo: Countries](https://ipinfo.io/countries)

- [IP2Location](https://lite.ip2location.com/ip-address-ranges-by-country)

- [IPDeny IP Blocks](https://www.ipdeny.com/ipblocks/)

- [Country IP Blocks](https://www.countryipblocks.net/acl.php)

- [herrbischoff: Country IP Blocks](https://github.com/herrbischoff/country-ip-blocks)

- [kaeferjaeger: IP Ranges](https://kaeferjaeger.gay/?dir=ip-ranges)

- [kaeferjaeger: CDN Ranges](https://kaeferjaeger.gay/?dir=cdn-ranges)