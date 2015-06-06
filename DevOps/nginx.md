# Nginx

* [Tutum's Nginx tag](https://learn.tutum.co/tag/12/nginx)
* [ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed)
* [How to install latest version of nginx](https://www.digitalocean.com/community/tutorials/how-to-install-the-latest-version-of-nginx-on-ubuntu-12-10)
* [Deploying Nginx with Docker](http://nginx.com/blog/deploying-nginx-nginx-plus-docker/)
* [Some nginx example](http://curtisz.com/someone-set-us-up-the-docker/)
* [A sample Docker workflow with Nginx, Node.js and Redis](http://anandmanisankar.com/posts/docker-container-nginx-node-redis-example/)
* [Virtual hosts on nginx](https://gist.github.com/soheilhy/8b94347ff8336d971ad0)
* [Some config to see](https://github.com/AmenZhou/ruby_on_rails_learning/blob/master/configs_and_setups.markdown)
* [Rate limiting with Nginx](https://lincolnloop.com/blog/rate-limiting-nginx/)
* [C10k](http://www.kegel.com/c10k.html)
* [Architecture of Nginx](http://www.aosabook.org/en/nginx.html)
* [Some Docker + Nginx example](http://blog.tryolabs.com/2015/03/26/configurable-docker-containers-for-multiple-environments/)

## PPA

```
▶ sudo apt-add-repository ppa:brightbox/ruby-ng

// https://nodesource.com/blog/nodejs-v012-iojs-and-the-nodesource-linux-repositories
▶ curl -sL https://deb.nodesource.com/setup_0.12 | sudo bash -
▶ sudo apt-get install nodejs
```

```
▶ sudo add-apt-repository ppa:nginx/stable
▶ sudo apt-get update
▶ sudo apt-get install nginx
▶ service nginx status

// Check for SPDY
▶ nginx -V
```

To test configuration file, use:

```
▶ nginx -t -c nginx.conf
```

## Location

Location is used to match the URI of the request. These locations may be nested or otherwise ordered to ensure that requests get routed to the right areas of the filesystem or application server.

## Reverse Proxy

A reverse proxy is a web server that terminates connections with clients and makes new ones to upstream servers on their behalf.

You have one common endpoint.

```
location / {
  include proxy.conf;
  proxy_pass http://localhost:8080;}
```

## Examples

**Very basic nginx.conf**

```
user www;
worker_processes 12; // CPU-bound and 12 cores
error_log /var/log/nginx/error.log;
pid /var/run/nginx.pid;
events {
  worker_connections 2048; // ???}

http {
  include /path/to/mime.types;
  default_type application/octet-stream;
  sendfile on;
  tcp_nopush on;
  tcp_nodelay on;
  keepalive_timeout 65;
  server_names_hash_max_size 1024;
  
  gzip on;
  gzip_http_version 1.0;
  gzip_comp_level 2;
  
  gzip_types text/plain text/css application/x-javascript text/xml application/xml application/xml+rss text/javascript application/javascript application/json;  

  gzip_disable msie6;
  
  # Define a virtual host
  server {
    listen 58.x.y.z:80 default_server;
    server_name jobline.com.sg;
    
    # Don't send Nginx version string
    server_tokens off;
    
    location {
        }  }}
```

**For sticky session**

```
upstream app {
  ip_hash; # Make it sticky
  server example1.com
  server example2.com}
```

```
server {
  listen 80;
  server_name jobline.com.sg www.jobline.com.sg;
  return 301 https://$host$request_uri;}

server {
  listen 443 ssl spdy;
  server_name jobline.com.sg www.jobline.com.sg;
  
  ssl on;
  ssl_certificate /etc/ssl/certs/server.crt;
  ssl_certificate_key /etc/ssl/private/server.key;
  ssl_session_timeout 5m;
  
  # Share the expensive SSL negotiation to all workers
  ssl_session_cache shared:WEB:10m;
  
  ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
  ssl_prefer_server_ciphers on;
  ssl_ciphers ???
  
  root ???;
  
  location ~/\. {
    deny all;  }
  
  # ~* is case-insensitive regular expression matching
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
    
    # X-FORWARDED-PROTO so that the upstream server can recognize
    # the fact that the origin request used HTTPS 
    proxy_set_header X-FORWARDED-PROTO https;
    
    proxy_set_header ssl_client_cert $ssl_client_cert;
    proxy_pass https://127.0.0.1:3000;  }}
```