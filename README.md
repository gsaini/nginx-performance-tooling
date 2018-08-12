# nginx - performance tooling...

Create self signed certificate to create secure server & place the cert & key on ssl folder on root.

`openssl req -x509 -newkey rsa:4096 -keyout nginx-selfsigned.key -out nginx-selfsigned.crt -days 365 -nodes` 

## How to start ngnix
`nginx -p ./  -c nginx.conf`

## How to stop nginx -  
`nginx -s stop  -p ./  -c nginx.conf`

## Browse -
Secure with HTTP v2 - https://localhost
Unsecure with HTTP v1.1 - http://localhost:3001

## Performance Reports (Lighthouse)
`./reports`