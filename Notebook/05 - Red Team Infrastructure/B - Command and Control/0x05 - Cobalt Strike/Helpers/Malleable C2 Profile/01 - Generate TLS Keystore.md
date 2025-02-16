---
author(s):
  - Userware
tags:
  - helpers
  - red-team-infrastructure
  - cobalt-strike
---
# 01 - Generate TLS Keystore

## 1.1 - Java Keytool

Modify in `teamserver` bash script.

```
$ keytool -keystore ./cobaltstrike.store -storepass <password> -keypass <password> -genkey -keyalg RSA -alias <alias_name> -dname "CN=www.website.com, OU=Company Inc., O=Company Name, L=San Francisco, S=California, C=US"

./TeamServerImage -Dcobaltstrike.server_port=50050 -Dcobaltstrike.server_bindto=0.0.0.0 -Djavax.net.ssl.keyStore=./cobalts
trike.store -Djavax.net.ssl.keyStorePassword=<password> teamserver $*
```

## 1.2 - OpenSSL

```
$ openssl req -new -newkey rsa:4096 -x509 -sha256 -days 365 -nodes -out public.crt -keyout private.key
..[omitted]..
Country Name (2 letter code) [AU]:US
State or Province Name (full name) [Some-State]:California
Locality Name (eg, city) []:San Francisco
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Pantheon Systems, Inc.
Organizational Unit Name (eg, section) []:
Common Name (e.g. server FQDN or YOUR name) []:pantheonsite.io
Email Address []:info@fortra.com

$ openssl req -new -key private.key -out domain.csr
Country Name (2 letter code) [AU]:US
State or Province Name (full name) [Some-State]:California
Locality Name (eg, city) []:San Francisco
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Pantheon Systems, Inc.
Organizational Unit Name (eg, section) []:
Common Name (e.g. server FQDN or YOUR name) []:pantheonsite.io
Email Address []:info@fortra.com

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:94c5a50b927c7234c3d347ea0da8a022
String too long, must be at most 20 bytes long
A challenge password []:94c5a50b92
An optional company name []:

$ openssl pkcs12 -export -in public.crt -inkey private.key -out domain.pkcs12 -passout:<source_keystore_password>
Enter Export Password:
Verifying - Enter Export Password:

$ keytool -importkeystore -deststorepass <destination_keystore_password> -destkeystore domain.store -srckeystore domain.pkcs12 -srcstoretype PKCS12 -srcstorepass <source_keystore_password>
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
Importing keystore domain.pkcs12 to domain.store...
Enter destination keystore password:
Re-enter new password:
Enter source keystore password:
Entry for alias 1 successfully imported.
Import command completed:  1 entries successfully imported, 0 entries failed or cancelled

$ rm domain.pkcs12
```

TODO: Shorten it

- You can shorten it.

```
$ openssl req -new -newkey rsa:4096 -x509 -sha256 -days 365 -nodes -subj "/C=<country_code>/ST=<state>/L=<locality>/O=<organization_name>/OU=<organization_unit>/CN=<domain.com>/emailAddress=<email>" -out public.crt -keyout private.key
```

## 1.3 - HTTP Certificate

```
https-certificate {
    # Option 1) Trusted and Signed Certificate
    # Use keytool to create a Java Keystore file. 
    # Refer to https://www.cobaltstrike.com/help-malleable-c2#validssl
    # or https://github.com/killswitch-GUI/CobaltStrike-ToolKit/blob/master/HTTPsC2DoneRight.sh
   
    # Option 2) Create your own Self-Signed Certificate
    # Use keytool to import your own self signed certificates

    #set keystore "/path/to/keystore.store";
    #set password "password";

    # Option 3) Cobalt Strike Self-Signed Certificate
	set C    "US"
	set CN   "www.website.com";
	set L    "San Francisco";
	set O    "Company Name";
	set OU   "Company Inc.";
	set ST   "California";
	set validity "365";
}
```