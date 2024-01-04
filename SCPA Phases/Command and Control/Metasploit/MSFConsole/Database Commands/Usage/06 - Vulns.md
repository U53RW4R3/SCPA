# 06 - Vulns

Search Tag(s): #metasploit-framework #command-and-control

## 6.1 - Help Menu

```
msf > vulns -h
Print all vulnerabilities in the database

Usage: vulns [addr range]


OPTIONS:

    -d, --delete             Delete vulnerabilities. Not officially supported.
    -h, --help               Show this help information.
    -i, --info               Display vuln information.
    -o, --output <filename>  Send output to a file in csv format.
    -p, --port <port>        List vulns matching this port spec.
    -R, --rhosts             Set RHOSTS from the results of the search.
    -S, --search <filter>    Search string to filter by.
    -s, --service <name>     List vulns matching these service names.

Examples:
  vulns -p 1-65536          # only vulns with associated services
  vulns -p 1-65536 -s http  # identified as http on any port
```

## 6.2 - Usage

TODO: Fill this info