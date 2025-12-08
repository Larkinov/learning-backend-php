# Утилиты Linux

Различные утилиты/программы для Linux

## Crontab
Крон есть крон

Записать логи crontab:
```bash
\* \* \* \* \* /home/user/test.sh >> /home/user/cron.log 2>&1
```

## Logrotate

Предназначена для автоматизации обработки журналов.

Этот файл содержит стандартные параметры и настраивает ротацию для нескольких логов, которые не принадлежат никаким системным пакетам
```bash
/etc/logrotate.conf
```

Узнать версию/проверить наличие:
```bash
logrotate --version
```

Выполнить конфигурацию:
```bash
logrotate -f file_configuration
```

Выполнить конфигурацию в дебаг режиме:
```bash
logrotate -d file_configuration
```

---

## JQ

Предназначена для работы с json файлами

Вывести данные:
```bash
jq . filename
```

Вывести определенный объект из файла:
```bash
jq '.object_name' filename
```

Примеры
```bash
jq '.object_name[2].property' filename
```

Вывести по очереди:
```bash
jq '.object_name[]' filename
```

Вывод json через входящую строку json:
```bash
echo "$json_string" | jq '.name'
```

Вставка аргумента в запрос:
```bash
jq --arg name "$name" '.domains[$name]' "$domains_config"
```

Условия:
```bash
jq --arg name "$name" '.domains[] |= if .name == $name then .property = "value" else . end' "$domains_config"
```