# nginx - performance tooling...

Create self signed certificate to create secure server & place the cert & key on ssl folder on root.

```
openssl req -x509 -newkey rsa:4096 -keyout nginx-selfsigned.key -out nginx-selfsigned.crt -days 365 -nodes
```

## How to start ngnix

```
nginx -p ./  -c nginx.conf
```

## How to stop nginx -  

```
nginx -s stop  -p ./  -c nginx.conf
```

## how to add brotli module in nginx

```
https://github.com/google/ngx_brotli
```

```
nginx -V
```

Copy everything after "configuration arguments:": ex -

```
--prefix=/usr/local/Cellar/nginx/1.15.7 --sbin-path=/usr/local/Cellar/nginx/1.15.7/bin/nginx --with-cc-opt='-I/usr/local/opt/pcre/include -I/usr/local/opt/openssl/include' --with-ld-opt='-L/usr/local/opt/pcre/lib -L/usr/local/opt/openssl/lib' --conf-path=/usr/local/etc/nginx/nginx.conf --pid-path=/usr/local/var/run/nginx.pid --lock-path=/usr/local/var/run/nginx.lock --http-client-body-temp-path=/usr/local/var/run/nginx/client_body_temp --http-proxy-temp-path=/usr/local/var/run/nginx/proxy_temp --http-fastcgi-temp-path=/usr/local/var/run/nginx/fastcgi_temp --http-uwsgi-temp-path=/usr/local/var/run/nginx/uwsgi_temp --http-scgi-temp-path=/usr/local/var/run/nginx/scgi_temp --http-log-path=/usr/local/var/log/nginx/access.log --error-log-path=/usr/local/var/log/nginx/error.log --with-debug --with-http_addition_module --with-http_auth_request_module --with-http_dav_module --with-http_degradation_module --with-http_flv_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_mp4_module --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module --with-http_slice_module --with-http_ssl_module --with-http_stub_status_module --with-http_sub_module --with-http_v2_module --with-mail --with-mail_ssl_module --with-pcre --with-pcre-jit --with-stream --with-stream_realip_module --with-stream_ssl_module --with-stream_ssl_preread_module
```

```
cd nginx-1.x.x
./configure --add-module=/path/to/ngx_brotli $copied-arguments
sudo make && sudo make install
```

## Browse -

Secure with HTTP v2 - https://localhost

Unsecure with HTTP v1.1 - http://localhost:3001

## Performance Reports (Lighthouse)

```
./reports
```
