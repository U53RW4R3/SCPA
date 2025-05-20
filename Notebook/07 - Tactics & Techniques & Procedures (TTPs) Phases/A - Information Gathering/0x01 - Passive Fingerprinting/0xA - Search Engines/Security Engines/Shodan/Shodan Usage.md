# Shodan Usage

## Usage Queries

```
port:<PORT>

hostname:<hostname>

os:<operating_system>

product:<product_name>

org:<organization_name>

asn:<asn_ID>

city:"<city_name>"

postal:"<postal_code>"

country:"<country_code>"

title:"<title>"

geo:<longitudes>,<latitudes>

net:<IP>/<CIDR>

tag:"<tag_name>"

vuln:"<cve_ID_number>"

before:"<mm/dd/yy>"

after:"<mm/dd/yy>"
```

## CLI Usage

How many credits you have left

```
$ shodan info
```

Perform query search.

```
$ shodan search <shodan_query>
```

Download results from the search query

```
$ shodan download output.json.gz <shodan_query>
```

Parse the fields after downloading a compressed JSON file.

```
$ shodan parse --fields ip_str,port,org,hostnames,has_vuln:true -O output.txt output.json.gz
```

Dump all of the DNS records when performing recon of the domain.

```
$ shodan domain domain.tld
```

Shodan perform query on the target.

```
$ shodan host <IP>
```

Receive the amount results in sum total

```
$ shodan count <shodan_query>
```

Check if the IP is a honeypot

```
$ shodan honeyscore <IP>
```

Display the statics of the internet

```
$ shodan stats <shodan_query>
```

---
## References

### Source Repositories

- [Shodan Filters](https://github.com/JavierOlmedo/shodan-filters)

- [Awesome Shodan Queries](https://github.com/jakejarvis/awesome-shodan-queries)

- [Shodan-Dorks](https://github.com/humblelad/Shodan-Dorks)

### Shodan

- [Shodan](https://shodan.io)

- [Shodan Examples](https://www.shodan.io/search/examples)

- [Shodan Search Query Fundamentals](https://help.shodan.io/the-basics/search-query-fundamentals)

- [Shodan Dorks - The God’s Eye](https://shahjerry33.medium.com/shodan-dorks-the-gods-eye-f224f9b3984f)

- [Secybr: Shodan.io Tutorials for Best Practices](https://secybr.com/posts/shodan-tutorials-for-best-practicies/)

- [Shodan Cheatsheet](https://thedarksource.com/shodan-cheat-sheet/)

- [HaXeZ Shodan Cheatsheet](https://haxez.org/wp-content/uploads/2022/06/HaXeZ_Shodan_Cheat_Sheet.pdf)

- [Cheatography Shodan](https://cheatography.com/sir-slammington/cheat-sheets/shodan/)

- [Techvomit.net Shodan cheat](https://techvomit.net/shodan-cheat/)

- [TurgenSec Shodan Pentesting Guide](https://kaliboys.com/wp-content/uploads/2018/11/Shodan-Pentesting-Guide-%E2%80%93kaliboys.pdf)