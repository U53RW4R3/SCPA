---
author(s):
  - Userware
tags:
  - helpers
  - red-team-infrastructure
---
# Whitelist IP Ranges

## #apache2

![[Blacklist IP Ranges#^5f791d]]

![[Blacklist IP Ranges#^8fdabf]]

Create a configuration file `/etc/apache2/ipwhitelist.conf` to whitelist list of IP addresses. Here's are a few examples.

```
# Allow single IP address
Require ip 104.18.27.120

# Allow multiple IP addresses
Require ip 104.18.27.120 142.250.202.14

# Allow netblocks
Require ip 104.18.27.120/24 142.250.202.14/24
```

![[Blacklist IP Ranges#^56e4f8]]

```
# Default to allow through all reverse proxies.
ProxyRequests Off
ProxyVia Off
<Proxy *>
    Require all granted
</Proxy>
 
# Block ip addresses in our ipwhitelist.conf file
<Location />
   <RequireAll>
      Include /etc/apache2/ipwhitelist.conf
   </RequireAll>
</Location>
 
# Add a 403 forbidden message for blacklisted ips

# Uncomment it if you only want to use inline HTML
# ErrorDocument 403 "<h3>Unusual activity has been detected from this IP address.</h3><p>As a consequence, access has been denied.</p><p>If you believe this is a mistake please contact me directly.</p>"

ErrorDocument 403 /var/www/html/error.html
```

![[Blacklist IP Ranges#^c78e4a]]

![[Blacklist IP Ranges#^e4e340]]

![[Blacklist IP Ranges#^109a9f]]

![[Blacklist IP Ranges#^5213fb]]

## #nginx

Create a configuration file `/etc/nginx/ipwhitelist.conf` to whitelist list of IP addresses.

```nginx
# Allow single IP address
allow 192.0.2.1;

# Allow single netblock
allow 203.0.113.0/24;
```

![[Blacklist IP Ranges#^89f36c]]

```nginx
http {
	# Hide server version
	server_tokens off;

	server {
	    listen 80; # Listening port
	    server_name yourdomain.com;

	    # Allow IP addresses in our ipwhitelist.conf file
	    include /etc/nginx/ipwhitelist.conf;

		# Uncomment it if you only want to use inline HTML
		# location @allow {
		#	default_type text/html;
		#	return 200 "<h3>Access granted. Welcome!</h3><p>You are allowed to access this server.</p>";
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

![[Blacklist IP Ranges#^5b6721]]

![[Blacklist IP Ranges#^122ae5]]

![[Blacklist IP Ranges#^bd6ae1]]

![[Blacklist IP Ranges#^271f69]]

## #caddy

Create a text file `/etc/caddy/ipwhitelist.txt` to whitelist list of IP addresses.

![[Blacklist IP Ranges#^29e9c7]]

![[Blacklist IP Ranges#^1a22f0]]

```
youdomain.com {
	# Hide server version
	header {
		-Server
	}

	# Allow IP addresses from an external list file
	@allowed_ips {
		file /etc/caddy/ipwhitelist.txt
	}

	# Uncomment it if you only want to use inline HTML
    # respond @allowed_ips "<h3>Access granted. Welcome!</h3><p>You are allowed to access this server.</p>"

    respond @allowed_ips 200 {
        # Optional: You can specify what to serve for allowed IPs here
    }


    respond @blocked_ips 403 {
	    file /var/www/html/error.html # Use the external error.html here
    }

    # Your regular site configuration continues here
    root * /var/www/html
    file_server
}
```

![[Blacklist IP Ranges#^e39b54]]

![[Blacklist IP Ranges#^d4e672]]