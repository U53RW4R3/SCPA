---
author(s):
  - Userware
tags:
  - command-line
  - cryptography
  - linux
---
# 04 - Certificates

## 4.1 - Check Remote Certificates

TODO: Rearrange under Active Fingerprinting

### 4.1.3 - XMPP Server

```
$ openssl s_client -showcerts -starttls xmpp -connect chat.example.com:5222
```

## 4.1 - Present Client Certificate

```
$ openssl s_client -showcerts -cert certificate.crt -key certificate.key -connect
```

## 4.2 - Verify Certificates

Verify Certificate with CA Certificate  
  
```  
$ openssl verify -verbose -CAFile ca.crt cert.crt  
```  
  
Verify Private Key Matches Certificate  
  
```  
$ openssl x509 -modulus -noout -in cert.crt | openssl md5  
  
$ openssl rsa -modulus -noout -in priv.key | openssl md5  
```

## 4.3 - Examine Certificates

Examine a **certificate request** (`.csr`).
  
```
$ openssl req -text -noout -verify -in old_certificate_request.csr
```

Examine a **private key** (`.key`).
  
```
$ openssl rsa -in private.key -check
```

Examine a **certificate** (`.crt`).

```
$ openssl x509 -in cert.crt -text -noout
```

Examine **PKCS** (`.pfx`) files.
  
```  
$ openssl pkcs12 -info -in key.pfx
```

## 4.4 - Generate Certificates

Generate RSA **private key** (`.key`) and **certificate request** (`.csr`).

```
$ openssl req -out new_request_certificate.csr -new -newkey rsa:4096 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email> -keyout private.key
```

Generate self-signed **certificate** (`.crt`) and **private key** (`.key`).

```
$ openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:4096 -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email> -keyout private.key -out certificate.crt
```

Generate **certificate request** (`.csr`) for existing **certificate** (`.crt`).

```
openssl x509 -x509toreq -in certificate.crt -out new_request_certificate.csr -signkey private.key
```

Generate **certificate request** (`.csr`) for existing **private key** (`.key`).

```
$ openssl req -out old_certificate_request.csr -key privvate.key -new
```

Create a **certificate authority** (`.ca`).

```
$ openssl req -new -x509 -extensions v3_ca -keyout certificate_authority.key -out certificate_authority.crt -days 365
```

Generate Diffie-Hellman keys.

```
$ openssl dhparam -out dhparam.pem <bits>
```