# Hydra

## 01 - Help Menu

```
$ pw-inspector -h
PW-Inspector v0.2 (c) 2005 by van Hauser / THC vh@thc.org [https://github.com/vanhauser-thc/thc-hydra]

Syntax: pw-inspector [-i FILE] [-o FILE] [-m MINLEN] [-M MAXLEN] [-c MINSETS] -l -u -n -p -s

Options:
  -i FILE    file to read passwords from (default: stdin)
  -o FILE    file to write valid passwords to (default: stdout)
  -m MINLEN  minimum length of a valid password
  -M MAXLEN  maximum length of a valid password
  -c MINSETS the minimum number of sets required (default: all given)
Sets:
  -l         lowcase characters (a,b,c,d, etc.)
  -u         upcase characters (A,B,C,D, etc.)
  -n         numbers (1,2,3,4, etc.)
  -p         printable characters (which are not -l/-n/-p, e.g. $,!,/,(,*, etc.)
  -s         special characters - all others not within the sets above

PW-Inspector reads passwords in and prints those which meet the requirements.
The return code is the number of valid passwords found, 0 if none was found.
Use for security: check passwords, if 0 is returned, reject password choice.
Use for hacking: trim your dictionary file to the pw requirements of the target.
Usage only allowed for legal purposes.
```

## 02 - Usage

TODO: Fill this info

---
## References

- [SQLServerCentral: Using pw-inspector in Brute Force attack on SQL Server](https://www.sqlservercentral.com/articles/using-pw-inspector-in-brute-force-attack-on-sql-server)