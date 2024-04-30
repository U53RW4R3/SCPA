# Shodan Usage

## Usage Queries

`HTTP Strict-Transport-Security`

`Apache`

`product:<product_name>`

`hostname:<website.com>`

`os:<operating_system>`

`port:<PORT>`

`org:<organization_name>`

`asn:<asn_ID>`

`city:"<city_name>"`

`postal:"<postal_code>"`

`country:"<country_code>"`

`title:"<title>"`

`geo:<longitudes>,<latitudes>`

`net:<IP>/<CIDR>`

`tag:"<tag_name>"`

`vuln:"<cve_ID_number>"`

`before:"<mm/dd/yy>"`

`after:"<mm/dd/yy>"`

## CLI Usage

- How many credits you have left

`$ shodan info`

- Perform query search

`$ shodan search <shodan_query>`

- Download results from the search query

`$ shodan download output.json.gz <shodan_query>`

- Parse the fields after downloading a compressed json file

`$ shodan parse --fields ip_str,port,org,hostnames,has_vuln:true -O output.txt output.json.gz`

- Must be all caps to fingerprint the domain

`$ shodan domain <DOMAIN.COM>`

- Shodan perform query on the target

`$ shodan host <IP>`

- Receive the amount results in sum total

`$ shodan count <shodan_query>`

- Check if the IP is a honeypot

`$ shodan honeyscore <IP>`

- Display the statics of the internet for example "samba"

`$ shodan stats <shodan_query>`

- Alerts

---
## References

- [Shodan](https://shodan.io)

- [Shodan Examples](https://www.shodan.io/search/examples)

- [Shodan Search Query Fundamentals](https://help.shodan.io/the-basics/search-query-fundamentals)

- [Shodan Filters](https://github.com/JavierOlmedo/shodan-filters)

- [Shodan Dorks - The God’s Eye](https://shahjerry33.medium.com/shodan-dorks-the-gods-eye-f224f9b3984f)

- [Secybr: Shodan.io Tutorials for Best Practices](https://secybr.com/posts/shodan-tutorials-for-best-practicies/)

- [Shodan Cheatsheet](https://thedarksource.com/shodan-cheat-sheet/)

- [Awesome Shodan Queries](https://github.com/jakejarvis/awesome-shodan-queries)

- [HaXeZ Shodan Cheatsheet](https://haxez.org/wp-content/uploads/2022/06/HaXeZ_Shodan_Cheat_Sheet.pdf)

- [Cheatography Shodan](https://cheatography.com/sir-slammington/cheat-sheets/shodan/)

- [Techvomit.net Shodan cheat](https://techvomit.net/shodan-cheat/)

- [TurgenSec Shodan Pentesting Guide](https://kaliboys.com/wp-content/uploads/2018/11/Shodan-Pentesting-Guide-%E2%80%93kaliboys.pdf)