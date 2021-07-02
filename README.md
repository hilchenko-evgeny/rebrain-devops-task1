В данном репозитории находится дефолтный конфигурационный файл nginx.conf, который был скачан с официального репозитория https://github.com/nginx/nginx/blob/master/conf/nginx.conf.

Partners nginx:
1. Amazon Web Services
2. Google Cloud Platform
3. IBM
4. Microsoft Azure
5. Red Hat

HTTP proxy and Web server features of nginx:
* Ability to handle more than 10,000 simultaneous connections with a low memory footprint (~2.5 MB per 10k inactive HTTP keep-alive connections)
* Handling of static files, index files and auto-indexing
* Reverse proxy with caching
* Load balancing with in-band health checks
* TLS/SSL with SNI and OCSP stapling support, via OpenSSL
* FastCGI, SCGI, uWSGI support with caching
* gRPC support since March 2018, version 1.13.10
* Name- and IP address-based virtual servers
* IPv6-compatible
* WebSockets since 1.3.13, including acting as a reverse proxy and do load balancing of WebSocket applications
* HTTP/1.1 Upgrade (101 Switching Protocols), HTTP/2 protocol support
* URL rewriting and redirection

NGINX it's a company. And here are the products of this company:

[NGINX Plus](https://www.nginx.com/products/nginx) \
[NGINX Controller](https://www.nginx.com/products/nginx-controller) \
[NGINX App Protect](https://www.nginx.com/products/nginx-app-protect) \
[NGINX Unit](https://www.nginx.com/products/nginx-unit) \
[NGINX Amplify](https://www.nginx.com/products/nginx-unit)

Logo NGINX:

![logo-nginx](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c5/Nginx_logo.svg/512px-Nginx_logo.svg.png)

Nginx and Apache both are the most popular web servers:
| Nginx | Apache |
| ------| ------ |
| free to use, open-source | free, open-source |
| multiple connections to single process | thread to connection |
| caches the static files | handle dynamic content internally |
| doesn’t support directory-level configuration | per-directory via .htaccess |
| third-party modules integrates in core | dynamically loadable modules |
| security controls out-of-the-box | only denial-of-service (DoS) security |
| better performance, multi-functional | suitable for shared hosting |

Example of configuration files Nginx and Apache via HTTP

Nginx:
```server {
    listen 80 default_server;
    server_name www.rebrainme.com;

    location /devops/ {
        root /var/www/html/rebrain-tasks;
        index index.html index.htm;
        try_files $uri $uri/ /index.html =404;
    }
    location /k8s/ {
        root /var/www/html/rebrain-k8s;
        index index.html index.htm;
        try_files $uri $uri/ /index.html =404;
    }
}```

Apache:
```Listen 80
NameVirtualHost *:80

SSLStrictSNIVHostCheck off

<VirtualHost *:80>
  DocumentRoot /var/www/html/rebrain
  ServerName www.rebrainme.com
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot /var/www/html/rebrain-lk
  ServerName www.lk.rebrainme.com
</VirtualHost>```