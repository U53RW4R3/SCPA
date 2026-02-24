# [[03 - Offensive Infrastructure/E - Setup Machine/0x03 - Offensive Tools/Reconnaissance/OSINT/Shef|Shef]]

> [!INFO]
> Doesn't require API key to scan targets.

By default the field will be displayed as an IP address.

```
$ shef -q "<query>"
```

Display the results through port number.

```
$ shef -q "<query>" -f port
```

Display subdomains.

```
$ shef -q <domain>.<tld> -f domain
```

Display the HTTP titles.

```
$ shef -q "<query>" -f http.title -json | jq
```

Display the results if the targets has a vulnerable software.

```
$ shef -q "<query>" -f vuln
```

## Use Cases

Collect live web servers.

```
$ shef -q "<query>" -f ip | sed 's/^/http\?:\/\//' | httpx -silent -o live-webservers.txt
```