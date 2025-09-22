# Сертификаты

### Certbot

Узнать дату окончания сертификата:

```bash
openssl x509 -enddate -noout -in /etc/letsencrypt/live/domain.com/fullchain.pem
```

Получить/обновить сертификат определенного домена (digitalocean):

```bash
sudo certbot certonly --dns-digitalocean --dns-digitalocean-credentials ./digitalocean.ini --dns-digitalocean-propagation-seconds 180 -d domain.com -d '*.domain.com';
```

Получить/обновить сертификат определенного домена (cloudeflare):

```bash
sudo certbot certonly   --dns-cloudflare   --dns-cloudflare-credentials /cloudflare.ini   --dns-cloudflare-propagation-seconds 180 -d domain.com -d *.domain.com
```

Получить сертификат через DNS-challenge:

```bash
sudo certbot --manual --preferred-challenges dns certonly -d domain.com -d '*.domain.com'
```

Получить сертификат через DNS acme:

```bash
certbot --manual --agree-tos --preferred-challenges dns certonly --server https://acme-v02.api.letsencrypt.org/directory -d *.domain.com -d domain.com
```
