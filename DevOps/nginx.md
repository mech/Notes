# Nginx

* [For Apache, good to know for Snow Leopard?](https://ninebark.net/2014/10/21/SSLConfig.html)
* [Apple don't even support TLS 1.2](http://apple.stackexchange.com/questions/211183/how-to-update-server-5-to-tls-1-2)
* [Quite a mess for Apple's Apache](https://codedmemes.com/lib/disable-sslv3-on-os-x-server-defeat-poodle/)

What can Nginx do:

* Proxy to Rails, Node application
* Software load balancer
* HTTP cache
* Off-load SSL
* Acts as SMTP, POP3 and IMAP
* Event-driven architecture and Reactor pattern
* Single-thread per worker process
* Multiplexing and event notifications

```
--prefix=/usr/local/Cellar/nginx/1.8.0
--conf-path=/usr/local/etc/nginx/nginx.conf

▶ sudo apt-get install build-essentials
▶ sudo apt-get install libpcre3 libpcre3-dev
▶ sudo apt-get install zlib1g zlib1g-dev
▶ sudo apt-get install openssl openssl-dev

▶ ./configure --conf-path=/etc/nginx/nginx.conf \
              --with-http_ssl_module \
              --with-http_spdy_module \
              --with-http_realip_module \
              --with-http_stub_status_module \
              --with-http_gzip_static_module \
              --with-google_perftools_module
              
▶ make
▶ sudo make install

// Find out where your nginx.conf file is at and test it
▶ nginx -t

// Ubuntu
/etc/nginx/nginx.conf

▶ kill -HUP `cat /var/run/nginx.pid`
▶ kill -HUP $(cat /var/run/nginx.pid)
```

Nginx master will run as root so that it can bind to port 80 and worker processes will run as least privileged user typically.

```
root      Ss   03:21   0:00 nginx: master process nginx -g daemon off;
nginx     S    03:21   0:00 nginx: worker process
```

The master process reads and executes the nginx configuration, binds the necessary ports, and runs the worker processes.

---

* [**Tips for deploying Nginx**](https://blog.docker.com/2015/04/tips-for-deploying-nginx-official-image-with-docker/)
* [**rails-nginx-unicorn**](https://github.com/seapy/dockerfiles/tree/master/rails-nginx-unicorn)
* [Nginx Tips](http://www.nginxtips.com/)
* [Tutum's Nginx tag](https://learn.tutum.co/tag/12/nginx)
* [ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed)
* [How to install latest version of nginx](https://www.digitalocean.com/community/tutorials/how-to-install-the-latest-version-of-nginx-on-ubuntu-12-10)
* [Deploying Nginx with Docker](http://nginx.com/blog/deploying-nginx-nginx-plus-docker/)
* [Some nginx example](http://curtisz.com/someone-set-us-up-the-docker/)
* [A sample Docker workflow with Nginx, Node.js and Redis](http://anandmanisankar.com/posts/docker-container-nginx-node-redis-example/)
* [Some config to see](https://github.com/AmenZhou/ruby_on_rails_learning/blob/master/configs_and_setups.markdown)
* [Rate limiting with Nginx](https://lincolnloop.com/blog/rate-limiting-nginx/)
* [C10k](http://www.kegel.com/c10k.html)
* [Architecture of Nginx](http://www.aosabook.org/en/nginx.html)
* [Some Docker + Nginx example](http://blog.tryolabs.com/2015/03/26/configurable-docker-containers-for-multiple-environments/)
* [Some nice example of the proxy docker-compose](http://devbandit.com/2015/05/29/vagrant-and-docker.html)
* [Django development with docker-compose](https://realpython.com/blog/python/django-development-with-docker-compose-and-machine/)
* [How to create your own website based on Docker](http://project-webdev.blogspot.de/2015/05/create-site-based-on-docker-part1.html)
* [Running a Nginx in a container](https://rubyplus.com/articles/2371)
* [Some nginx example](http://tech.yunojuno.com/trifecta-part-2-docker)
* [Nginx + Passenger](https://gist.github.com/mikhailov/711913)

## fail2ban and ModSecurity

Can docker provide these 2 functionality also?

Or we send container nginx log to syslog and let host's fail2ban to process that?

See http://stackoverflow.com/questions/36180792/how-to-make-fail2ban-read-json-docker-logs

## SSL

* [HTTPS Performance Tuning](http://blog.httpwatch.com/2009/01/15/https-performance-tuning/)
* [SSL Cipher](http://security.stackexchange.com/questions/54639/recommended-ssl-ciphers-for-security-compatibility-perfect-forward-secrecy)
* [Let's Encrypt](https://letsencrypt.org/)
* [Automate buying of SSL](https://sslmate.com/)
* [Deploying HTTPS](https://www.youtube.com/watch?v=9WuP4KcDBpI)

To concatenate primary certificate and intermediate certificate:

```
▶ cat jobline.com.sg.crt RapidSSLCA.crt >> bundle.crt

ssl on;
ssl_certificate bundle.crt
ssl_certificate_key jobline.com.sg.key
```

Strict-Transport-Security: max-aga=31536000; includeSubDomains

## nginx.conf

* [**server-configs-nginx**](https://github.com/h5bp/server-configs-nginx)
* [Best nginx configuration?](https://gist.github.com/plentz/6737338)
* [Unicorn example from defunkt](https://github.com/defunkt/unicorn/blob/master/examples/nginx.conf)
* [**nginx-boilerplate**](https://github.com/Umkus/nginx-boilerplate)

2 types of directives: Simple Directives and Context Directives

```
worker_processes 6; # 6-core, 12 Hyper-Threading

// Context Directive
events {
  worker_connections 1024;}

http {
  server {
    // Simple Directive
    listen *:80 ssl backlog=511;  }	}
```

There is an implied main context. Nginx also has a lightweight inheritance model where you can overwrite previously defined directives in nested contexts.

## Location

Location is used to match the URI of the request. These locations may be nested or otherwise ordered to ensure that requests get routed to the right areas of the filesystem or application server.

There are 3 types of location patterns: simple, exact, and regular expression.

```
# Simple
location /images {
  root /usr/local/html/images;}

# Will serve from folder /data/images for URL matching http://host/gifs/a.gif
location /gifs/ {
  alias /data/images/;}

# Not very useful, will match exactly, but is quick to search
location = /foobar/images/a.gif {}

# Case-sensitive
location ~ \.(gif|jpg)$ {}

# Case-insensitive
location ~* \.(gif|jpg)$ {}

# Non-regular expression, if found, skip any regular expression coming next
location ^~ /foobar/images {}

# Cache API related requests for 10m
location /api {
  expires 10m;}
```

## Assets

```
location ~* \.(css|js|gif|jpe?g|png)$ {
  expires 168h;}
```

## tcp_nodelay, tcp_nopush

* [Some nice discussion](https://news.ycombinator.com/item?id=9045125)

## Virtual Hosting

1 public IP with many different domains.

```
server_name 'api.jobline.com.sg'

server_name 'jobline.com.sg'
```

## Passenger 5

* [Running a Rails app on Docker using the Passenger image](https://rossfairbanks.com/2015/03/06/rails-app-on-docker-using-passenger-image.html)

```
▶ passenger-config --root
▶ rbenv which ruby
```

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

## Reverse Proxy

Unlike Apache with mod_php, Nginx do not embed interpreter into the webserver. Instead it delegate to a separate server and proxies upstream.

A Load Balancer is in fact a Reverse Proxy!

Sub-URL vs Sub-Domain, Multiple apps

* [**docker-nginx-loadbalancer**](https://github.com/jasonwyatt/docker-nginx-loadbalancer)
* [**Nginx proxy for Docker containers**](http://blog.danivovich.com/2015/07/09/nginx-proxy-for-docker-containers/)
* [Virtual hosts on nginx](https://gist.github.com/soheilhy/8b94347ff8336d971ad0)
* [Using Nginx as a reverse proxy/load balancer with Weave and Docker](http://weave.works/guides/weave-docker-nginx-ubuntu-simple.html)
* [How to setup Rails with Puma and Nginx](http://ruby-journal.com/how-to-setup-rails-app-with-puma-and-nginx/)
* [Multiple Rails 4 apps using Nginx and Unicorn](http://stackoverflow.com/questions/18134046/multiple-rails-4-app-using-nginx-unicorn)
* [**Sub-URL vs sub-domain**](http://www.redmine.org/projects/redmine/wiki/Sub_URI_for_multisites_at_one_domain)
* [Nginx, Unicorn and multiple Rails apps](http://jrochelly.com/post/2013/08/nginx-unicorn-multiple-rails-apps/)
* [Hosting rails on sub-uri](http://stackoverflow.com/questions/19594542/hosting-rails-app-on-thins-nginx-on-a-sub-uri-behind-a-reverse-proxy)
* [How to create your own website based on Docker with Nginx reverse proxy](http://project-webdev.blogspot.de/2015/06/create-site-based-on-docker-part10-nginx-reverse-proxy-docker-image.html)
* [Nginx, node, redis example](http://anandmanisankar.com/posts/docker-container-nginx-node-redis-example/)

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
  listen 58.124.12.8:80; // Can listen multiple ports
  listen 58.124.12.8:443 ssl spdy;
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

## Security

* [Hardening Nginx](https://www.acunetix.com/blog/articles/nginx-server-security-hardening-configuration-1/)
* [Gist for self-signed cert](https://gist.github.com/hansode/1121067)
* [Is TLS fast yet?](https://istlsfastyet.com/)

```
// Remove passphrase
▶ openssl rsa -in original.key -out unencripted.key
```

## Performance and Linux tuning

* [How to optimize Nginx configuration](https://www.digitalocean.com/community/tutorials/how-to-optimize-nginx-configuration)
* [Some nice benchmark example](https://www.youtube.com/watch?v=FJrs0Ar9asY)
* [Tuning Nginx for best performance](http://dak1n1.com/blog/12-nginx-performance-tuning/)
* [Nginx optimization: Understanding TCP_NODELAY and TCP_NOPUSH](https://t37.net/nginx-optimization-understanding-sendfile-tcp_nodelay-and-tcp_nopush.html)

```
// 1000 requests
// 100 concurrency
▶ ab -n 1000 -c 100 http://22.22.22.4/

▶ brew install httperf
▶ httperf --server 192.168.1.10 --port 80 --uri /index.html --rate 300 --num-conn 30000 --num-call 1 --timeout 5
```

Kernel flags set with `sysctl` tool will be lost upon reboot. In order to persist them, you must add them to `/etc/sysctl.conf` or `/etc/sysctl.d/`.


## Videos

* [5 things you didn't know Nginx could do](https://www.youtube.com/watch?v=7Y7ORypoHhE)