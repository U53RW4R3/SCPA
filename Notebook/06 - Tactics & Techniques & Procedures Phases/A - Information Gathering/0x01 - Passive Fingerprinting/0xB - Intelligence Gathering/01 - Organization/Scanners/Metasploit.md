# Metasploit

## Lookup Name

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

msf auxiliary(gather/corpwatch_lookup_name) > set limit <int>

msf auxiliary(gather/corpwatch_lookup_name) > run company_name="<organization_name>" [year=<year>]
```

## Lookup ID

```
msf > use auxiliary/gather/corpwatch_lookup_id

msf auxiliary(gather/corpwatch_lookup_id) > options

msf auxiliary(gather/corpwatch_lookup_id) >
```