# 01 - Generate TLS Keystore

Search Tag(s): #red-team-infrastructure #cobalt-strike #helpers

- Modify in `teamserver` bash script.

```
keytool -keystore ./cobaltstrike.store -storepass <password> -keypass <password> -genkey -keyalg RSA -alias <alias_name> -dname "CN=www.website.com, OU=Company Inc., O=Company Name, L=San Francisco, S=California, C=US"

./TeamServerImage -Dcobaltstrike.server_port=50050 -Dcobaltstrike.server_bindto=0.0.0.0 -Djavax.net.ssl.keyStore=./cobalts
trike.store -Djavax.net.ssl.keyStorePassword=<password> teamserver $*
```

## 01 - HTTP Certificate

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