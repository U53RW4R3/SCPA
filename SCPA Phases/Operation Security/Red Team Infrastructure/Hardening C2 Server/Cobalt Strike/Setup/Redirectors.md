# Redirectors


TODO: Fill this information

## 01 - Apache2

`$ sudo a2enmod rewrite`

`$ cat /etc/apache2/sites-available/redirect.conf`

- For Debian/Ubuntu

`/etc/apache2/apache2.conf` or `/etc/apache2/sites-available/000-default.conf`

- For CentOS/RHEL

`/etc/httpd/conf/httpd.conf` or `/etc/httpd/conf.d/proxy.conf`

```
<VirtualHost *:80>
    # ServerName example.com  # Replace with your domain or IP address
	ServerName <C2_IP>
    ServerAlias <C2_IP>

    ProxyPass / http://<C2_IP>:<C2_PORT>/
    ProxyPassReverse / http://<C2_IP>:<C2_PORT>/
</VirtualHost>
```

```
$ sudo a2enmod proxy && \
sudo a2enmod proxy_http && \
sudo systemctl restart apache2
```

`$ sudo a2ensite redirect`

`$ sudo ln -s /etc/apache2/sites-available/cobalt_strike.conf /etc/apache2/sites-enabled/`

`$ sudo service apache2 restart`

```
sudo yum install mod_proxy mod_proxy_http && \
sudo systemctl restart httpd
```

## 02 - Nginx

`$ cat /etc/nginx/sites-available/default`

---

```
server {
    listen 80;
    # server_name redirector-domain.com;  # Replace with your redirector domain
    server_name _;

	# Cobalt Strike IP and Port
    set $cobalt_strike_ip "<C2_IP>";
    set $cobalt_strike_port "<C2_PORT>";

    location / {
        proxy_pass http://$cobalt_strike_ip:$cobalt_strike_port;  # Replace with your Cobalt Strike team server IP and port
        # proxy_set_header Host $host;
        # proxy_set_header X-Real-IP $remote_addr;
    }
}
```

- For HTTPS listener

`$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/ssl/cobaltstrike.key -out /etc/nginx/ssl/cobaltstrike.crt`

```
server {
    listen 443 ssl;
    # server_name redirector.domain.com;
    server_name _;

	# Cobalt Strike IP and Port
    set $cobalt_strike_ip "<C2_IP>";
    set $cobalt_strike_port "<C2_PORT>";

    ssl_certificate /etc/nginx/ssl/cobaltstrike.crt;
    ssl_certificate_key /etc/nginx/ssl/cobaltstrike.key;

    location / {
        proxy_pass https://$cobalt_strike_ip:$cobalt_strike_port;
        # proxy_set_header Host $host;
        # proxy_set_header X-Real-IP $remote_addr;
    }
}
```

`$ sudo ln -s /etc/nginx/sites-available/cobaltstrike_redirect /etc/nginx/sites-enabled/`

`$ sudo nginx -t`

`$ sudo service nginx restart`

---
## References

- [WhiteOakSecurity: Cobalt Strike OpSec](https://www.whiteoaksecurity.com/blog/cobalt-strike-opsec/)

- [High Reputation Redirectors and Domain Fronting](https://www.cobaltstrike.com/blog/high-reputation-redirectors-and-domain-fronting/)

- [HTTPS Payload and C2 Redirectors](https://bluescreenofjeff.com/2018-04-12-https-payload-and-c2-redirectors/)

- [Red Team Insights on HTTPS Domain Fronting Google Hosts Using Cobalt Strike](https://www.cyberark.com/resources/threat-research-blog/red-team-insights-on-https-domain-fronting-google-hosts-using-cobalt-strike)