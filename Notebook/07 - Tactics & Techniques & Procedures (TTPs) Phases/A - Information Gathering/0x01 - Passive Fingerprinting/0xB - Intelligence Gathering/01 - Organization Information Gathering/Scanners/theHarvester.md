# theHarvester

## Setup

### Dependencies

Install the required dependencies according to your package manager.

```
$ sudo apt install -y pipx python3.11-venv python3-aiodns python3-aiofiles python3-aiohttp python3-aiosqlite python3-bs4 python3-certifi python3-dateutil python3-dnspython python3-fastapi python3-lxml python3-netaddr python3-ujson python3-types-pyyaml python3-requests python3-retrying python3-shodan python3-uvicorn

$ pip install aiomultiprocess censys playwright slowapi
```

### Install theHarvester

```
$ git clone https://github.com/laramies/theHarvester.git

$ pipx install --python python3.11

$ pipx ensurepath
```

## Help Menu

```
$ theHarvester -h
Created default proxies.yaml at /home/user/.theHarvester/proxies.yaml
*******************************************************************
*  _   _                                            _             *
* | |_| |__   ___    /\  /\__ _ _ ____   _____  ___| |_ ___ _ __  *
* | __|  _ \ / _ \  / /_/ / _` | '__\ \ / / _ \/ __| __/ _ \ '__| *
* | |_| | | |  __/ / __  / (_| | |   \ V /  __/\__ \ ||  __/ |    *
*  \__|_| |_|\___| \/ /_/ \__,_|_|    \_/ \___||___/\__\___|_|    *
*                                                                 *
* theHarvester 4.6.0                                              *
* Coded by Christian Martorella                                   *
* Edge-Security Research                                          *
* cmartorella@edge-security.com                                   *
*                                                                 *
*******************************************************************
usage: theHarvester [-h] -d DOMAIN [-l LIMIT] [-S START] [-p] [-s] [--screenshot SCREENSHOT] [-v] [-e DNS_SERVER] [-t] [-r [DNS_RESOLVE]] [-n] [-c] [-f FILENAME] [-b SOURCE]

theHarvester is used to gather open source intelligence (OSINT) on a company or domain.

options:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Company name or domain to search.
  -l LIMIT, --limit LIMIT
                        Limit the number of search results, default=500.
  -S START, --start START
                        Start with result number X, default=0.
  -p, --proxies         Use proxies for requests, enter proxies in proxies.yaml.
  -s, --shodan          Use Shodan to query discovered hosts.
  --screenshot SCREENSHOT
                        Take screenshots of resolved domains specify output directory: --screenshot output_directory
  -v, --virtual-host    Verify host name via DNS resolution and search for virtual hosts.
  -e DNS_SERVER, --dns-server DNS_SERVER
                        DNS server to use for lookup.
  -t, --take-over       Check for takeovers.
  -r [DNS_RESOLVE], --dns-resolve [DNS_RESOLVE]
                        Perform DNS resolution on subdomains with a resolver list or passed in resolvers, default False.
  -n, --dns-lookup      Enable DNS server lookup, default False.
  -c, --dns-brute       Perform a DNS brute force on the domain.
  -f FILENAME, --filename FILENAME
                        Save the results to an XML and JSON file.
  -b SOURCE, --source SOURCE
                        anubis, baidu, bevigil, binaryedge, bing, bingapi, bufferoverun, brave, censys, certspotter, criminalip, crtsh, dnsdumpster, duckduckgo, fullhunt, github-code,
                        hackertarget, hunter, hunterhow, intelx, netlas, onyphe, otx, pentesttools, projectdiscovery, rapiddns, rocketreach, securityTrails, sitedossier,
                        subdomaincenter, subdomainfinderc99, threatminer, tomba, urlscan, virustotal, yahoo, zoomeye
```

## Usage

```
$ theHarvester -l 1000 -d <domain.tld | organization_name>
```

To include API keys it is located at `theHarvester/data/api-keys.yaml`.

```
$ theHarvester -l 1000 -d <domain.tld | organization_name> -s <source_1>,<source_n>
```

To bypass rate-limit it's best to use proxies. When running the program for the first time it should reveal the default location and if it doesn't exist it'll create one like this `/home/$USER/.theHarvester/proxies.yaml`.

```
$ theHarvester -p -l 1000 -d <domain.tld | organization_name>
```

To gather information about the organization.

```
$ theHarvester -l 1000 -d "<organization_name>" -b brave,baidu,bing,duckduckgo,yahoo,linkedin -f output.json

$ theHarvester -l 1000 -d "<organization_name>" -b brave,baidu,bing,bingapi,duckduckgo,yahoo,twitter,linkedin -f output.json
```

---
## References

- [theHarvester](https://github.com/laramies/theHarvester)