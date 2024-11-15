---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - sliver
  - redirectors
---
# Redirectors

TODO: Fill this information

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

TODO: Test the .htaccess file

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

`sliver > http -L <C2_IP> -l <C2_PORT> -d <redirector_IP>`

### 1.4 - HTTPS

- For HTTPS listener

```
$ sudo a2enmod ssl

$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/private.key -out /etc/apache2/ssl/certificate.crt
```

---

```
$ sudo nano /etc/apache2/sites-available/default-ssl.conf
<IfModule mod_ssl.c>
    <VirtualHost *:<C2_PORT>>
        # ServerName <C2_IP>
        # ServerAlias <C2_IP>

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/certificate.crt
        SSLCertificateKeyFile /etc/apache2/ssl/private.key

        ProxyPass / http://<C2_IP>:<C2_PORT>/
        ProxyPassReverse / http://<C2_IP>:<C2_PORT>/
    </VirtualHost>
</IfModule>
```

`$ sudo systemctl restart apache2`

`sliver > https -L <C2_IP> -l <C2_PORT> -d <redirector_IP>`

## 02 - Nginx

`$ cat /etc/nginx/sites-available/sliver_c2`

---

```
server {
    listen 80;
    # server_name < _ | C2_IP >;
    server_name _;

    location / {
        try_files $uri $uri/ @c2;
    }

    location @c2 {
        proxy_pass http://<C2_IP>:<C2_PORT>/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

server {
    listen 443 ssl;
    listen [::]:443 ssl http2;
    # server_name < _ | C2_IP >;
    server_name _;

    ssl_certificate /etc/nginx/ssl/nginx.crt;
    ssl_certificate_key /etc/nginx/ssl/nginx.key;

    location / {
        try_files $uri $uri/ @c2;
    }

    location @c2 {
        proxy_pass http://<C2_IP>:<C2_PORT>/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

```
$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/ssl/private.key -out /etc/nginx/ssl/certificate.crt

$ sudo ln -s /etc/nginx/sites-available/sliver_c2 /etc/nginx/sites-enabled/

$ sudo nginx -t

$ sudo service nginx restart
```

Once you've setup the redirectors properly. Refer to the [[Setting Up Redirectors and Firewall Rules|section for setting up a firewall rule to apply it]].