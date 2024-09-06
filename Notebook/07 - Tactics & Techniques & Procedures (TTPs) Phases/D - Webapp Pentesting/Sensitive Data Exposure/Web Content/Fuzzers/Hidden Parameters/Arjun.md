# Arjun

## Setup

### Install Dependencies

In Debian/Ubuntu-based distros

```
$ sudo apt install -y python3-setuptools python3-requests python3-dicttoxml
```

### Install Arjun

```
$ git clone https://github.com/s0md3v/Arjun /opt/intelligence-gathering/Arjun && \
cd Arjun && sudo python3 setup.py install
```

## Help Menu

```
$ arjun -h
usage: arjun [-h] [-u URL] [-o JSON_FILE] [-oT TEXT_FILE] [-oB [BURP_PORT]] [-d DELAY] [-t THREADS] [-w WORDLIST] [-m METHOD] [-i [IMPORT_FILE]] [-T TIMEOUT] [-c CHUNKS] [-q]
             [--headers [HEADERS]] [--passive [PASSIVE]] [--stable] [--include INCLUDE] [--disable-redirects]

options:
  -h, --help            show this help message and exit
  -u URL                Target URL
  -o JSON_FILE, -oJ JSON_FILE
                        Path for json output file.
  -oT TEXT_FILE         Path for text output file.
  -oB [BURP_PORT]       Port for output to Burp Suite Proxy. Default port is 8080.
  -d DELAY              Delay between requests in seconds. (default: 0)
  -t THREADS            Number of concurrent threads. (default: 5)
  -w WORDLIST           Wordlist file path. (default: {arjundir}/db/large.txt)
  -m METHOD             Request method to use: GET/POST/XML/JSON/HEADERS. (default: GET)
  -i [IMPORT_FILE]      Import target URLs from file.
  -T TIMEOUT            HTTP request timeout in seconds. (default: 15)
  -c CHUNKS             Chunk size. The number of parameters to be sent at once
  -q                    Quiet mode. No output.
  --headers [HEADERS]   Add headers. Separate multiple headers with a new line.
  --passive [PASSIVE]   Collect parameter names from passive sources like wayback, commoncrawl and otx.
  --stable              Prefer stability over speed.
  --include INCLUDE     Include this data in every request.
  --disable-redirects   disable redirects
```

## Usage

TODO: Fill this info and I got this covered - Userware

```
$ arjun -u "<URL>" -oT hidden-endpoints-output.txt
```

```
$ arjun -i urls.txt -oT hidden-endpoints-output.txt
```


---
## References

- [Arjun](https://github.com/s0md3v/Arjun)

- [Arjun Usage](https://github.com/s0md3v/Arjun/wiki/Usage)

- [Bug Bounty: Find Hidden Parameters](https://hacktivator.medium.com/bug-bounty-find-hidden-parameters-ea219b01e7ca)

- [The Hacker Recipes: HTTP parameter pollution](https://www.thehacker.recipes/web/inputs/http-parameter-pollution)

- [Discover Hidden HTTP Parameters to Find Weaknesses in Web Apps](https://null-byte.wonderhowto.com/how-to/discover-hidden-http-parameters-find-weaknesses-web-apps-0212025)