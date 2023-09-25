### в /etc/environment нужно добавить переменные  
FKS_PORT  
SUP_PORT  
MEDOC_PORT  

### Создание dhparam  
`openssl dhparam -out ~/projects/.nginx/dhparam.d/fks.pem 2048`
`openssl dhparam -out ~/projects/.nginx/dhparam.d/sup.pem 2048`
`openssl dhparam -out ~/projects/.nginx/dhparam.d/medoc.pem 2048`

### Создание сертификатов  
```
docker compose run --rm certbot certonly \
--webroot --webroot-path /var/www/certbot/ \ 
-m <email> --agree-tos \
-d comma,separated,domains
```