# Drupwn

Search Tag(s): #drupal #webapp

TODO: Fill this info

## Setup

## Help Menu

```
$ drupwn -h

        ____
       / __ \_______  ______ _      ______
      / / / / ___/ / / / __ \ | /| / / __ \
     / /_/ / /  / /_/ / /_/ / |/ |/ / / / /
    /_____/_/   \__,_/ .___/|__/|__/_/ /_/
                     /_/

usage: drupwn [-h] [--mode MODE] [--target TARGET] [--users] [--nodes] [--modules] [--dfiles] [--themes]
              [--version VERSION] [--cookies COOKIES] [--thread THREAD]
              [--range RANGE] [--ua UA] [--bauth BAUTH]
              [--delay DELAY] [--log] [--update] 
              [--proxy PROXY | --proxies PROXIES]

Drupwn aims to automate drupal information gathering.

optional arguments:
  -h, --help         show this help message and exit
  --mode MODE        enum|exploit
  --target TARGET    hostname to scan
  --users            user enumaration
  --nodes            node enumeration
  --modules          module enumeration
  --dfiles           default files enumeration
  --themes           theme enumeration
  --version VERSION  Drupal version
  --cookies COOKIES  cookies
  --thread THREAD    threads number
  --range RANGE      enumeration range
  --ua UA            User Agent
  --bauth BAUTH      Basic authentication
  --delay DELAY      request delay
  --log              file logging
  --update           update plugins and themes
  --proxy PROXY      [http|https|socks]://host:port
  --proxies PROXIES  Proxies file
```

## Usage

---
## References

- [Drupwn](https://github.com/immunIT/drupwn)