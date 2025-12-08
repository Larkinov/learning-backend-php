# Переменные окружения

## Сервер (Ubuntu)

Добавить для всего сервера:
```
nano /etc/environment

MY_ENV_1='LALA';
```

Добавить для PHP-FPM:
```
nano /etc/php/VERSION/fpm/pool.d/NAME_POOL (для сайтов обычно www.conf)

MY_ENV_1='LALA'
```

