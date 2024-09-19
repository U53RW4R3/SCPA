# GoWitness

## 01 - Setup

```
$ go install github.com/sensepost/gowitness@latest && \
sudo mv ~/go/bin/gowitness /usr/local/bin/
```

## 02 - Help Menu

```
$ gowitness
A commandline web screenshot and information gathering tool by @leonjza

Usage:
  gowitness [command]

Available Commands:
  file        screenshot URLs sourced from a file or stdin
  help        Help about any command
  nmap        Screenshot services from an Nmap XML file
  report      Work with gowitness reports
  scan        Scan a CIDR range and take screenshots along the way
  server      Starts a webservice that takes screenshots
  single      Take a screenshot of a single URL
  version     Prints the version of gowitness

Flags:
  -D, --db-path string           destination for the gowitness database (default "gowitness.sqlite3")
      --debug                    enable debug logging
      --disable-db               disable all database operations
      --disable-logging          disable all logging
  -F, --fullpage                 take fullpage screenshots
  -h, --help                     help for gowitness
  -X, --resolution-x int         screenshot resolution x (default 1440)
  -Y, --resolution-y int         screenshot resolution y (default 900)
  -P, --screenshot-path string   store path for screenshots (use . for pwd) (default "screenshots")
      --timeout int              preflight check timeout (default 10)
      --user-agent string        user agent string to use (default "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.102 Safari/537.36")

Use "gowitness [command] --help" for more information about a command.
```

## 03 - Usage

TODO: Fill this info

```
$ gowitness single -P /path/to/directory/ --no-http
```

```
$ gowitness scan -P /path/to/directory/ --no-http
```

```
$ gowitness file -f urls.txt -P /path/to/directory/ --no-http
```

```
$ gowitness nmap -P /path/to/directory/ --no-http
```

---
## References

- [Gowitness](https://github.com/sensepost/gowitness)