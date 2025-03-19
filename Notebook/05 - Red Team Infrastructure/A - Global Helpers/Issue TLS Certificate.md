---
author(s):
  - Userware
tags:
  - helpers
  - red-team-infrastructure
  - "#T1001-003"
---
# Issue TLS Certificate

```
$ sudo apt install -y ca-certificates

$ sudo dnf install -y ca-certificates

$ sudo pacman --noconfirm -S ca-certificates
```

```
/etc/ssl/certs/
```

```
$ echo | openssl s_client -servername <target_IP> -connect <target_IP>:443 2>/dev/null | openssl x509 -noout -issuer -subject -dates
```

## Add Self-Signed Certificate

```
$ openssl -req -new -x509 -nodes -out cert.crt -keyout private.key

$ cat private.key cert.crt > fullchain.pem
```

## Impersonate TLS Certificate

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

msf auxiliary(gather/impersonate_ssl) > run rhosts=<target_IP> [verbose=true]
```

---
## References

- [Certbot](https://certbot.eff.org/)

- [Let's Encrypt](https://letsencrypt.org/)

- [Cloudflare Free SSL/TLS](https://www.cloudflare.com/application-services/products/ssl/)

- [ZeroSSL](https://zerossl.com/)

- [SSLShopper](https://www.sslshopper.com/ssl-certificate-list.html)

- [Jeff Atkinson: Fingerprinting Encrypted](https://old.zeek.org/brocon2018/slides/Jeff_Atkinson._Fingerprinting_Encrypted.pptx)