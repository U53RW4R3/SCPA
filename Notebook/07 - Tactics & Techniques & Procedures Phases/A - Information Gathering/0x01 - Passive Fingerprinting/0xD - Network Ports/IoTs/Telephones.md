# Telephones

## Polycom

```
http.title:"- Polycom" "Server: lighttpd"

"Polycom Command Shell" -failed port:23
```

```
msf > use exploits/unix/misc/polycom_hdx_auth_bypass

msf > use exploits/unix/misc/polycom_hdx_traceroute_exec
```

https://staaldraad.github.io/2017/11/12/polycom-hdx-rce/

https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/exploit/unix/misc/polycom_hdx_traceroute_exec.md