---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - metasploit-framework
  - redirectors
---
# Redirectors

## 01 - Apache2

### 1.1 - Config file

```
$ cat /etc/apache2/apache2.conf
<Directory /var/www/>
		Options Indexes FollowSymLinks
		AllowOverride All
		Require all granted
</Directory>
```

### 1.2 - .htaccess file config

TODO: Fill this info

`R=302` means redirect.

```
$ cat /var/www/html/.htaccess
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/stage$
RewriteRule ^.*$ http://<C2_IP>%{REQUEST_URI} [P]
RewriteRule ^.*$ http://<domain.com>/? [L,R=302]
$ chmod 644 /var/www/html/.htaccess
```

### 1.3 - HTTP

```
$ sudo a2enmod rewrite proxy proxy_http && \
sudo systemctl restart apache2
```

`$ sudo a2ensite 000-default.conf`

Here is the configuration.

```
$ cat /etc/apache2/sites-available/000-default.conf
<VirtualHost *:<C2_PORT>>
	# ServerName <C2_IP>
	# ServerAlias <C2_IP>
	DocumentRoot /var/www/html

	ProxyRequests Off
	ProxyPass / http://<C2_IP>:<C2_PORT>/
	ProxyPassReverse / http://<C2_IP>:<C2_PORT>/
</VirtualHost>
```

`$ sudo systemctl restart apache2`

```
msf >
```

### 1.4 - HTTPS

- For HTTPS listener

`$ sudo a2enmod ssl`

`$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt`

---

```
$ sudo nano /etc/apache2/sites-available/default-ssl.conf
<IfModule mod_ssl.c>
    <VirtualHost *:<C2_PORT>>
        # ServerName <C2_IP>
        # ServerAlias <C2_IP>

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.crt
        SSLCertificateKeyFile /etc/apache2/ssl/apache.key

        ProxyPass / http://<C2_IP>:<C2_PORT>/
        ProxyPassReverse / http://<C2_IP>:<C2_PORT>/
    </VirtualHost>
</IfModule>
```

`$ sudo systemctl restart apache2`

```
msf >
```

Once you've setup the redirectors properly. Refer to the [[Setting Up Redirectors and Firewall Rules|section for setting up a firewall rule to apply it]].