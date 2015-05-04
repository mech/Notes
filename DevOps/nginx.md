# Nginx

* [Tutum's Nginx tag](https://learn.tutum.co/tag/12/nginx)
* [ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed)

```
server {
  listen 80;
  server_name jobline.com.sg www.jobline.com.sg;
  return 301 https://$host$request_uri;}
server {
  listen 443;
  server_name jobline.com.sg www.jobline.com.sg;
  
  ssl on;
  ssl_certificate /etc/ssl/certs/server.crt;
  ssl_certificate_key /etc/ssl/private/server.key;
  ssl_session_timeout 5m;
  
  ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
  ssl_prefer_server_ciphers on;
  ssl_ciphers ???
  
  root ???;
  
  location ~/\. {
    deny all;  }
  
  location ~* ^/(css|fonts|img|js)/.+$ {
    gzip_static on;
    gzip_vary on;
    expires 30d;
    add_header Pragma public;
    add_header Cache-Control "public";  }
  
  location ~* ^(robots|humans)\.txt$ {
    expires 30d;
    add_header Pragma public;
    add_header Cache-Control "public";
  }
  
  location / {
    # auth_basic on;
    # auth_basic_user_file /www/httpd.auth;
    proxy_pass http://127.0.0.1:3000;  }}
```