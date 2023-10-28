# Setup

Search Tag: #red-team-infrastructure #sliver

## 1.1 - Teamserver

`$ sudo systemctl stop sliver`

`$ cat /root/.sliver/configs/server.json`

---

```json
{
    "daemon_mode": true,
    "daemon": {
        "host": "",
        "port": <PORT>
    },
    "logs": {
        "level": 4,
        "grpc_unary_payloads": false,
        "grpc_stream_payloads": false,
        "tls_key_logger": false
    },
    "jobs": {
        "multiplayer": null
    },
    "watch_tower": null,
    "go_proxy": ""
```

`$ sudo systemctl daemon-reload`

`$ sudo systemctl start sliver`

## 1.2 - Firewall Rules

```
# mkdir /etc/iptables
# iptables -I INPUT 1 -p tcp -s 0.0.0.0/0 --dport <PORT> -j DROP
# iptables -I INPUT 1 -p tcp -s 127.0.0.1 --dport <PORT> -j ACCEPT
# iptables-save > /etc/iptables/rules.v4
```

- A script to autorun after reboot. Run this as root (without `sudo`)

```bash
cat << EOF > /etc/rc.firewall-rules
#!/bin/sh -e
#
# rc.firewall-rules
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo iptables-restore < /etc/iptables/rules.v4

exit 0
EOF
```

`$ sudo chmod +x /etc/rc.firewall-rules`

## 1.3 - Redirectors

TODO: Fill this information

### 1.3.1 - Apache2

```
$ sudo a2enmod proxy && \
sudo a2enmod proxy_http && \
sudo service apache2 restart
```

`$ sudo a2enmod rewrite`

`$ sudo nano /etc/apache2/sites-available/sliver_c2_port80.conf`

---

```
<VirtualHost *:80>
    ServerName <C2_IP>
    ServerAlias <C2_IP>

    ProxyPass / http://<C2_IP>:<C2_PORT>/
    ProxyPassReverse / http://<C2_IP>:<C2_PORT>/
</VirtualHost>
```

`$ sudo ln -s /etc/apache2/sites-available/sliver_c2_port80.conf /etc/apache2/sites-enabled/`

- For HTTPS listener

`$ sudo a2enmod ssl`

`$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt`

`$ sudo nano /etc/apache2/sites-available/sliver_c2_port443.conf`

---

```
<IfModule mod_ssl.c>
    <VirtualHost *:443>
        ServerName <C2_IP>
        ServerAlias <C2_IP>

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.crt
        SSLCertificateKeyFile /etc/apache2/ssl/apache.key

        ProxyPass / http://<C2_IP>:<C2_PORT>/
        ProxyPassReverse / http://<C2_IP>:<C2_PORT>/
    </VirtualHost>
</IfModule>
```

`$ sudo ln -s /etc/apache2/sites-available/sliver_c2_port443.conf /etc/apache2/sites-enabled/`

`$ sudo service apache2 restart`

### 1.3.2 - Nginx

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
$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/ssl/nginx.key -out /etc/nginx/ssl/nginx.crt

$ sudo ln -s /etc/nginx/sites-available/sliver_c2 /etc/nginx/sites-enabled/

$ sudo nginx -t

$ sudo service nginx restart
```


### 1.3.3 - Domain Fronting

TODO: Provide usage example for domain fronting in Sliver C2 and using certs to encrypt by evading JARM hashes

`sliver > https`