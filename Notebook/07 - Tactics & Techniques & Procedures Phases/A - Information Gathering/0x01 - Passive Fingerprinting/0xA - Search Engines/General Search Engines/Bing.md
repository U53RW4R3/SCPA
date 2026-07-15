# Bing

## 01 - `bing-ip2hosts`

### 1.1 - Setup

Install the dependencies

```
$ sudo apt install -y wget
```

Install the script.

```
$ sudo wget -qO /usr/local/bin/bing-ip2hosts https://raw.githubusercontent.com/urbanadventurer/bing-ip2hosts/master/bing-ip2hosts && \
sudo chmod 755 /usr/local/bin/bing-ip2hosts
```

### 1.2 - Help Menu

```
$ bing-ip2hosts -h
  m,                   .,recon:,        ,,
  #####               ]##""^^"%##m    %##b
  ####b               ]##      `##b
  ####b               ]##       ##    i##    @#b,######m       ,######m ##b
  ####b 1mw,          ]##MMM####      i##    ]###`    %##     ###`    `@##
  ####b  1#####Nw,    ]##``    @#b    i##    ]##       ###   ###       j##
  ####i   %########[  ]##       @##   i##    ]##       ###   ##g       j##
  ####n      2#####[  ]##      @##    i##    ]##       ###   @##       {##
  ####g  ,#########b  ]##   ,,e###    j##    ]##       ###    7##m,,,s#M##
  #############M^     'WWWWWW%b^       ii    'nn       nn*      `1337` g##
  ##########"                                                          G##
    "%##"                                                     @#Gmmem###G
  ,i                ,s2e,     ##                                  ````
   `               "`   %#    ##                             T#
  ]#   ]#,#M5@#p         #b   #H#H%@#     s#M5O#o   ,#MSSM  W@##W=  s#SSW
  ]#   j#p    ^#p      ,#M    ##    @#   ##'   'O#  S#,      ]#     #b
  ]#   j#      #M    ,#M      ##    @#   #o     O#    "SXm   ]#      ^"@#
  ]#   j##,  ,##   ,#2        ##    @#   7#.   .#O  ,   ]#   ]#Q       ,#s
  ]#   j######'    #######x   ##    @#    s#####o    ####^    #Tt    ####^
       j#
       j#          bing-ip2hosts (1.0.5) by Andrew Horton @urbanadventurer
       j#          https://morningstarsecurity.com/research/bing-ip2hosts
                   https://github.com/urbanadventurer/bing-ip2hosts

bing-ip2hosts is a Bing.com web scraper that discovers websites by IP address.
Use for OSINT and discovering attack-surface of penetration test targets.

Usage: ./bing-ip2hosts [OPTIONS] IP|hostname

OPTIONS are:
-o FILE	Output hostnames to FILE.
-i FILE	Input list of IP addresses or hostnames from FILE.
-n NUM	Stop after NUM scraped pages return no new results (Default: 5).
-l	Select the language for use in the setlang parameter (Default: en-us).
-m	Select the market for use in the setmkt parameter (Default is unset).
-u	Only display hostnames. Default is to include URL prefixes.
-c	CSV output. Outputs the IP and hostname on each line, separated by a comma.
-q	Quiet. Disable output except for final results.
-t DIR	Use this directory instead of /tmp.
-V	Display the version number of bing-ip2hosts and exit.
```

### 1.3 - Usage

```
$ bing-ip2hosts -o output.txt <IP>

$ bing-ip2hosts -o output.txt <hostname>
```

Scrape more results with new pages.

```
$ bing-ip2hosts -n <number_of_pages> -o output.txt <hostname>
```

Display only hostnames with a URL prefix

```
$ bing-ip2hosts -u -o output.txt <hostname>
```

---
## References

- [Bing](http://www.bing.com)

- [Bing-IP2Hosts](https://morningstarsecurity.com/research/bing-ip2hosts)

- [Bing-IP2Hosts Source Repository](https://github.com/urbanadventurer/bing-ip2hosts)