# GetAllURLs

## 01 - Setup

```
$ go install github.com/lc/gau/v2/cmd/gau@latest && \
sudo mv ~/go/bin/gau /usr/local/bin/
```

## 02 - Help Menu

```
$ gau -h                                                        
Usage of gau:
      --blacklist strings   list of extensions to skip
      --fc strings          list of status codes to filter
      --fp                  remove different parameters of the same endpoint
      --from string         fetch urls from date (format: YYYYMM)
      --ft strings          list of mime-types to filter
      --json                output as json
      --mc strings          list of status codes to match
      --mt strings          list of mime-types to match
      --o string            filename to write results to
      --providers strings   list of providers to use (wayback,commoncrawl,otx,urlscan)
      --proxy string        http proxy to use
      --retries uint        retries for HTTP client
      --subs                include subdomains of target domain
      --threads uint        number of workers to spawn (default 1)
      --timeout uint        timeout (in seconds) for HTTP client (default 45)
      --to string           fetch urls to date (format: YYYYMM)
      --verbose             show verbose output
      --version             show gau version
```

## 03 - Usage

TODO: Fill this info

```
$ gau <URL_1> <URL_2> <URL_n> --o urls-output.txt
```

`$ cat domains.txt | gau`

```
$ printf example.com | gau
$ cat domains.txt | gau --threads 5
$ gau example.com google.com
$ gau --o example-urls.txt example.com
$ gau --blacklist png,jpg,gif example.com
```

## 04 - Use Cases

---
## References

- [Gau (GetallURLs)](https://github.com/lc/gau)