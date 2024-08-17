# SQLMap

## Google Dork Endpoints

```
$ sqlmap -g "inurl:\"<parameter>=\" [site:website.com] ext:\(php \| aspx \| asp \| jsp \| js\) inurl:&?" --cookies="<google_cookies_session>" -f --random-agent
```

## Syntax Error SQL Dorks

```
$ sqlmap -g "inurl:\".php?id=1\" intext:\"You have an error in your SQL syntax\"" --cookies="<google_cookies_session>" --random-agent
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x01 - Passive Fingerprinting/0xA - Search Engines/General Search Engines/Google Dorking/Dorks/Web Enumeration/SQL Injection/Manual|Information Gathering: Google Dorking - Manual SQL Injection]]