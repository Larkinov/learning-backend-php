# Docker
## Про конфигурацию
[Инструкции выполнения - CMD, RUN, ENTRYPOINT](https://habr.com/ru/companies/nixys/articles/830830/)

## Работа с контейнером
Перезагрузить контейнер:
```bash
docker restart name_container
```
Получить подробную информацию о контейнере:

```bash
docker inspect name_container
```

## Настройки
Ограничение по CPU и RAM:
```bash
docker run --cpus="0.5" --memory="256m" NAME_IMAGE
```

## Сети
[Статья на хабре](https://habr.com/ru/companies/otus/articles/730798/)

Узнать текущие сети Docker:

```bash
docker network ls
```
Удалить сеть:

```bash
docker network rm NAME
```
## Разное
Скопировать файл из контейнера на хост-машину:

```bash
docker cp name_container:/file/path/container /file/path/host
```
Скопировать файл из хост-машины в контейнер:

```bash
docker cp /file/path/host name_container:/file/path/container
```
# Docker Compose
## Параметры конфигурации
[Параметры конфигурации .yml](https://docs.docker.com/reference/compose-file/)

Добавление «специальной обработки инициализации контейнера» (убивает зомби-процессы):

```yaml
init: true
```
Использование env-файла (использование через ${NAME}, использовать можно и внутри конфигурации):
```yaml
env_file:
   - .env
```
## Использование нескольких контейнеров
Объединение контейнеров происходит на уровне создания сетей Docker.

Использовать внешнюю сеть:
```yaml
services:
  NAME_SERVICE:
    networks:
      NAME

networks:
  network_name:
    name: NAME
    external: true
```