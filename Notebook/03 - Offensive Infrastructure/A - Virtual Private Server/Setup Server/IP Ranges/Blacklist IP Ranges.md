---
author(s):
  - Userware
tags:
  - helpers
  - red-team-infrastructure
---
# Blacklist IP Ranges

## #apache2

Hide the web server's software version in `/etc/apache2/apache2.conf`. ^5f791d

```
# Turn off apache version info displaying
ServerSignature Off
ServerTokens Prod
```

^8fdabf

Create a configuration file `/etc/apache2/ipblacklist.conf` to blacklist list of IP addresses.

```
# Deny single IP address
Require not ip 192.0.2.1

# Deny multiple IP addresses
Require not ip 192.0.2.1 192.0.4.5

# Deny netblocks
Require not ip 192.0.2.1/24 192.0.4.5/24
```

Then add the following configuration in `/etc/apache2/apache2.conf`. ^56e4f8

```
# Default to allow through all reverse proxies.
ProxyRequests Off
ProxyVia Off
<Proxy *>
    Require all granted
</Proxy>

# Block ip addresses in our ipblacklist.conf file
<Location />
   <RequireAll>
      Require all granted
      Include /etc/apache2/ipblacklist.conf
   </RequireAll>
</Location>
 
# Add a 403 forbidden message for blacklisted ips

# Uncomment it if you only want to use inline HTML
# ErrorDocument 403 "<h3>Unusual activity has been detected from this IP address.</h3><p>As a consequence, access has been denied.</p><p>If you believe this is a mistake please contact me directly.</p>"

ErrorDocument 403 /var/www/html/error.html
```

Check if the apache's configuration is correct. ^c78e4a

```
# apache2ctl configtest
```

^e4e340

Then reload the apache server's configuration. ^109a9f

```
# systemctl reload apache2
```

^5213fb

## #nginx

Create a configuration file `/etc/nginx/ipblacklist.conf` to blacklist list of IP addresses.

```nginx
# Deny single IP address
deny 192.0.2.1;

# Deny single netblock
deny 192.0.2.1/24;
```

Then add the following configuration in `/etc/nginx/nginx.conf`. ^89f36c

```nginx
http {
	# Hide server version
	server_tokens off;

	server {
	    listen 80; # Listening port
	    server_name yourdomain.com;

	    # Block IP addresses in our ipblacklist.conf file
	    include /etc/nginx/ipblacklist.conf;

		# Uncomment it if you only want to use inline HTML
		# location @deny {
		#	default_type text/html;
		#	return 403 "<h3>Unusual activity has been detected from this IP address.</h3><p>As a consequence, access has been denied.</p><p>If you believe this is a mistake please contact me directly.</p>";
		#}

	    location / {
	        error_page 403 /error.html; # Specify the error page here
	    }

	    location /error.html {
		    root /var/www/html; # Path of the DocumentRoot
		    internal;           # Prevent direct access
	    }
	}
}
```

Check if the nginx's configuration is correct. ^5b6721

```
# nginx -t
```

^122ae5

Then reload the nginx server's configuration. ^bd6ae1

```
# systemctl reload nginx
```

^271f69

## #caddy

Create a text file `/etc/caddy/ipblacklist.txt` to blacklist list of IP addresses.

```
# Single IP address
remote_ip 192.0.2.1

# Single netblock
remote_ip 192.0.2.1/24
```

^29e9c7

Then add the following configuration in `Caddyfile`. ^1a22f0

```
youdomain.com {
	# Hide server version
	header {
		-Server
	}

	# Block IP addresses from an external list file
	@blocked_ips {
		file /etc/caddy/ipblacklist.txt
	}

	# Uncomment it if you only want to use inline HTML
    # respond @blocked_ips "<h3>Unusual activity has been detected from this IP address.</h3><p>As a consequence, access has been denied.</p><p>If you believe this is a mistake please contact me directly.</p>" 403

    respond @blocked_ips 403 {
	    file /var/www/html/error.html # Use the external error.html here
    }

    # Your regular site configuration continues here
    root * /var/www/html
    file_server
}
```

Then reload the caddy server's configuration. ^e39b54

```
# caddy reload
```

^d4e672

---
## References

### Source Repositories

- [curi0usJack: `.htaccess`](https://gist.github.com/curi0usJack/971385e8334e189d93a6cb4671238b10)
 
 ![[06 - Tactics & Techniques & Procedures Phases/E - Hacking The Cloud/Cloud Providers/01 - Information Gathering/Passive/AWS/Dorks#^2cb0fa|Dorks]]

### Wizcrafts

- [Wizcrafts: Block Access to Your Website with a `.htaccess` Blocklist](https://www.wizcrafts.net/htaccess-blocklists.html)

### Open Dynamic Block Lists

- [Open Dynamic Block Lists](https://www.opendbl.net)

### Jay Ta'ala

- [Jay Ta'ala: Securing Apache and blocking a list of ip addresses](https://me.jaytaala.com/securing-apache-and-blocking-a-list-of-ip-addresses/)