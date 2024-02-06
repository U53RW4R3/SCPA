# Manual

Search Tag(s): #dvwa #xss #sql-injection 

TODO: Demonstrate with [[02 - Interact Session|toxssin]] to inject javascript code

CTRL+SHIFT+C

## Persistent XSS

Harvests data

### Poor Man's Cookie Harvester

TODO: Make a javascript to steal credentials and post it in the guestbook message board.

## Exploit Chaining

^a7f343

TODO: Come up ways of exploit chaining in webapps

### Poor Man's Cookie Harvester

#### Insert XSS payload in the DBMS to collect cookies

Same thing with user account persistence but leveraging it as a XSS attack in SQLi

XSS and SQLi is another way to do perform stored XSS which also can be performed for phishing to replace legitimate URLs to malicious links.

An example if you discover a e-commerce website when a user browses the site to select items:

`INSERT INTO cart VALUES('Coffee', '<script>alert(1)</script>', 15)`

#### Store cookies in a database field via XSS attacks

### Initial Foothold

#### Waterfall

Finally, demonstrate a **waterfall** attack vector by utilizing metasploit framework autopwn module to exploit outdated programs such windows web browser.

---
## References

- [Computer Security Student (CSS): Man-in-the-Middle, Persistent Covert Cross Site Scripting Injection #2](https://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson15/index.html)

- [StationX: How to Use the BeEF Hacking Tool](https://www.stationx.net/beef-hacking-tool/)

- [SecurityIdiots: URL Spoofed Phishing using SQLi](https://securityidiots.com/Web-Pentest/SQL-Injection/url-spoofed-phishing-with-sqli.html)

- [SecurityIdiots: XSS Injection with SQLi (XSSQLi)](https://securityidiots.com/Web-Pentest/SQL-Injection/xss-injection-with-sqli-xssqli.html)