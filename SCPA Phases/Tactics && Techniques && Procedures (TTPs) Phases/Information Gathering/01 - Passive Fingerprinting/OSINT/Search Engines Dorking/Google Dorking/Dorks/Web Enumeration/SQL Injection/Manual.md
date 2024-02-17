# SQL Injection

## Top parameters

```
?id=
?cid=
?uid=
?iddesc=
?page=
?pageid=
?page_id=
?dir=
?search=
?item=
?itemid=
?cart=
?cartid=
?book=
?bookid=
?pid=
?prodid=
?profileid=
?category=
?categoryid=
?idcategory=
?file=
?class=
?url=
?news=
?item=
?menu=
?lang=
?name=
?ref=
?title=
?view=
?topic=
?news=
?newsid=
?thread=
?type=
?date=
?form=
?join=
?main=
?nav=
?region=
?cat=
?catalog=
?catid=
?cat_id=
?catalogid=
```

## Login Panels

```
admin panel
login
admin login
password

inurl:(login | signin | auth) intitle:(Login | "sign in")
```

## Error-Based SQL Injection Dorks

```
inurl:index.php?id=1'

site:website.com ext:(php | aspx)

intext:("sql syntax near" | "syntax error has occurred" | "incorrect syntax near" | "unexpected end of SQL command" | "Warning: mysql_connect()" | "Warning: mysql_query()" | "Warning: pg_connect()")

intext:("You have an error in your SQL syntax" | "PHP Parse error" | "PHP Warning" | "PHP Error")
```

---
## References

- [Top25-parmameter: SQL injection](https://github.com/lutfumertceylan/top25-parameter/blob/master/SQLi-parameters.txt)

- [GBHackers: New Google Dorks List Collection for SQL Injection – 2023](https://gbhackers.com/latest-google-sql-dorks/)

- [GBHackers: SQLMap Detecting and Exploiting SQL Injection](https://gbhackers.com/sqlmap-detecting-exploiting-sql-injection/)

- [Google Dork Cheat Sheet for Finding Hidden Admin Panels](https://medium.com/@cuncis/google-dork-cheat-sheet-for-finding-hidden-admin-panels-379e3414d486)

- [Admin Panel Dorks](https://github.com/cyberm0n/admin-panel-dorks)

- [HOW TO FIND ADMIN PANEL OF WEBSITE USING GOOGLE DORKS?](https://coolzgeeks.com/how-to-find-admin-panel-using-google-dorks/)

- [DorkSearch.com](https://dorksearch.com/)

### Gathering SQL Injection Vulnerabilities

- [Threat Intelligence: How to find vulnerabilities in a web page in 10 minutes](https://medium.com/@Threat_Intelligence/how-to-find-vulnerabilities-in-a-web-page-in-10-minutes-66cd052b4fbc)