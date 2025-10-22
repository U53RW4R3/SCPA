# Dorkscout

## 01 - Setup

```
$ go install github.com/R4yGM/dorkscout@latest && \
sudo mv ~/go/bin/dorkscout /usr/local/bin
```

## 02 - Help Menu

### 2.1 - Main Options

```
$ dorkscout -h
Usage:
  dorkscout [command]

Available Commands:
  completion  generate the autocompletion script for the specified shell
  delete      deletes all the .dorkscout files inside a given directory
  help        Help about any command
  install     installs a list of dorks from exploit-db.com
  scan        scans a specific website or all the websites it founds for a list of dorks

Flags:
  -h, --help   help for dorkscout

Use "dorkscout [command] --help" for more information about a command.
```

### 2.2 - Scan Options

```
$ dorkscout scan -h        
makes google searches with dorks in a given list that will then be parsed into different
readable formats such as HTML or .txt, this function contains also support proxy ip rotation to
avoid getting blocked or rate limited by google.

Usage:
  dorkscout scan [flags]

Flags:
  -l, --Limit int           The limit of results you get from a single dork (default 100)
  -O, --Output string       file path where you want to save the results in a normal format
  -H, --OutputHTML string   file path where you want to save the results in a HTML format
  -d, --dorklist string     dorklists path separated by a comma
  -h, --help                help for scan
  -x, --proxy string        HTTP, HTTPS or SOCKS5 proxy to use in the requests
  -t, --target string       site or website to scan for dorks
```
## 03 - Usage

TODO: Fill this info

Install a list of google dorks from exploit-db

```
$ dorkscout install --output-dir /path/to/new/directory
```

Use a specific dork to gather URLs

```
$ dorkscout scan -d="/path/to/new/directory/Web Server Detection.dorkscout"
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/B - Vulnerability Assessment/02 - Public Exploits/ExploitDB/Usage/02 - Basic|ExploitDB]]

- [dorkscout](https://github.com/R4yGM/dorkscout)