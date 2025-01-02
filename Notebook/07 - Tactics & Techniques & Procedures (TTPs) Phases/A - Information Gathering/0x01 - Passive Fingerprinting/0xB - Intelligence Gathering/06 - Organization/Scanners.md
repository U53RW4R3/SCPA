# Scanners

## [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xB - Intelligence Gathering/01 - Gathering URLs/Scanners/theHarvester|theHarvester]]

```
$ theHarvester -l 1000 -d "<organization_name>" -b brave,baidu,bing,duckduckgo,yahoo,linkedin -f output.json

$ theHarvester -l 1000 -d "<organization_name>" -b brave,baidu,bing,bingapi,duckduckgo,yahoo,twitter,linkedin -f output.json
```

## Metasploit

```
msf > use auxiliary/gather/corpwatch_lookup_name

msf auxiliary(gather/corpwatch_lookup_name) > options

Module options (auxiliary/gather/corpwatch_lookup_name):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   COMPANY_NAME                       yes       Search for companies with this name
   CORPWATCH_APIKEY                   no        Use this API key when getting the data
   LIMIT             5                yes       Limit the number of results returned
   YEAR              2021             no        Year to look up

msf auxiliary(gather/corpwatch_lookup_name) > set company_name <organization_name>

msf auxiliary(gather/corpwatch_lookup_name) > set limit <int>

msf auxiliary(gather/corpwatch_lookup_name) > run
```