# [[03 - Offensive Infrastructure/E - Setup Machine/0x02 - Offensive Tools/Password Cracking/Online/GoMapEnum|GoMapEnum]]

```
$ GoMapEnum gather searchEngine -c <organization_name> -f '{first}.{last}@domain.com' -e

$ GoMapEnum gather searchEngine -c <organization_name> -f '{f}.{last}@domain.com' -e

$ GoMapEnum gather searchEngine -c <organization_name> -f "{f}{last}@domain.com" -e

$ GoMapEnum gather searchEngine -c <organization_name> -f '{first}.{l}@domain.com' -e

$ GoMapEnum gather searchEngine -c <organization_name> -f '<DOMAIN>\{first}.{last}' -e
```