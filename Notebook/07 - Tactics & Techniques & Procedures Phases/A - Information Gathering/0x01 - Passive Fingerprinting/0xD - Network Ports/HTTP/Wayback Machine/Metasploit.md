# Metasploit

```
msf > use auxiliary/scanner/http/enum_wayback

msf auxiliary(scanner/http/enum_wayback) > options 

Module options (auxiliary/scanner/http/enum_wayback):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   DOMAIN                    yes       Domain to request URLS for
   OUTFILE                   no        Where to output the list for use


View the full module info with the info, or info -d command.

msf auxiliary(scanner/http/enum_wayback) > set domain <domain.com>

msf auxiliary(scanner/http/enum_wayback) > set outfile [/path/to/file.txt]

msf auxiliary(scanner/http/enum_wayback) > run
```