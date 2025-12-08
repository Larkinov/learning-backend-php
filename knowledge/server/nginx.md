# Nginx

## Официальная документация

[Документация](https://nginx.org/ru/docs/)
[Конфигурации](https://github.com/elasticweb/nginx-configs?tab=readme-ov-file|)

## Быстрые команды

Узнать версию nginx

```bash
nginx -v
```

Узнать с какими флагами был установлен NGINX

```bash
nginx -V
```

Проверка конфигурационного файла на синтаксис

```bash
nginx -t
```

Перезагрузка

```bash
nginx -s reload
```

Статус NGINX

```bash
systemctl status nginx
```

## API GATEWAY

[Хорошее объяснение как развернуть шлюз для API на NGINX](https://www.f5.com/company/blog/nginx/deploying-nginx-plus-as-an-api-gateway-part-1|)

## Пароли

Стандартный путь до файла с паролями:

```bash
/etc/nginx/.htpasswd
```

Создание имени, а затем пароля в .htpasswd (при установленном OpenSSL):

```bash

sudo sh -c "echo -n 'NAME:' >> PATHFILE"
sudo sh -c "openssl passwd -6 PASSWORD >> PATHFILE"

```

Использование .htpasswd в блоке location:

```bash

auth_basic "Restricted Content";
auth_basic_user_file PATHFILE;

```

## Реальные IP адреса

[Официальная документация](https://nginx.org/en/docs/http/ngx_http_realip_module.html)

При получении проксированных ip адресов, эти запросы получают заголовок в которой есть значение реального ip адреса. Чтобы получить его необходимо прописать такие команды:

Добавить доверенный ip адрес:

```bash

set_real_ip_from 192.168.1.0/24;
set_real_ip_from 2001:0db8::/32;

```

Поле заголовка запроса, который заменяет ip адрес:

```bash

real_ip_header X-Forwarded-For;

```

Использовать ли значение из заголовка или использовать предоставленный проксируемый ip адрес:

```bash

real_ip_recursive on/off;

```

## gzip

[Официальная документация](https://nginx.org/ru/docs/http/ngx_http_gzip_module.html#gzip_min_length)

gzip - сжатие данных перед отправкой клиенту

Для получения gzip ответа, необходимо добавить заголовок **-H "Accept-Encoding: gzip"**. Однако, современные браузеры добавляют его автоматически (не проверял это утверждение). То есть, если необходимо будет проверить работу gzip не через браузер, то нужно не забыть добавить этот заголовок.

включить/выключить модуль

```bash
gzip on/off;
```

работать ли с проксируемыми данными: any - работать со всеми проксируемыми данными

```bash
gzip_proxied any;
```

уровень сжатия (от 1 до 9):

```bash
gzip_comp_level 1;
```

число и размер буферов для выполнения сжатия:

```bash
gzip_buffers 16 8k;
```

пропускать данные длина которых меньше в байтах:

```bash
gzip_min_length 256;
```

с какими MIME-type работать:

```bash
gzip_types text/plain text/css application/json application/javascript;
```
