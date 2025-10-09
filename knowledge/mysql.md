# MySQL

## Официальная документация

[MySQL](https://dev.mysql.com/doc/)

## Установка

```Dockerfile
FROM mysql:8.4.4
ENV MYSQL_ROOT_PASSWORD=pass
ENV MYSQL_DATABASE=name
ENV MYSQL_USER=user
ENV MYSQL_PASSWORD=user_pass
```

Быстрый запуск

```
docker run --name name-container -v name-container:/var/lib/mysql -p 33060:33060 name-container -d
```

## CLI

войти:

```bash
mysql -u root -p BASENAME
```

## Система/Настройки

Вывод системных переменных:

```sql
SHOW VARIABLES
```

Вывод определенной системной переменной:

```sql
SHOW VARIABLES LIKE 'name'
```

[Включение логов](https://blog.devart.com/how-to-enable-mysql-query-log.html)

Включить логи через CLI:

```sql
SET GLOBAL general_log = 'ON'
```

Задать файл логов через CLI:

```sql
SET GLOBAL general_log_file = '/path/file/log'
```

## Пользователи

Создать:

```sql
CREATE USER 'user'@'location' IDENTIFIED BY 'password'
```

Удалить:

```sql
  DROP USER 'user'@'location'
```

Показать пользователей:

```sql
SELECT user,host FROM mysql.user
```

Смена пароля пользователя:

```sql
  SELECT user,host FROM mysql.user
```

## Привилегии

Типы привилегий:

- все

```sql
ALL PRIVILEGES
```

Добавить:

```sql
GRANT priveleges_type ON table_name TO 'user'@'location'
```

Удалить:

```sql
  REVOKE priveleges_type ON table_name from 'user'@'location'
```

Показать привилегии пользователя:

```sql
SHOW GRANTS for 'user'@'location'

```

Обновить привилегии:

```sql

FLUSH PRIVILEGES

```

## Базы данных

Узнать все БД

```sql

SHOW DATABASES

```

Создать БД

```sql

CREATE DATABASE NAME_DB

```

Использовать в запросах БД:

```sql

USE DB_NAME

```

## Типы данных

### Ключи

Первичный ключ:

```sql

PRIMARY KEY (name_vield)

или при изменении таблицы

ALTER TABLE table_name
ADD PRIMARY KEY (name_vield);

```

Пример для ID:

```sql

id int primary key auto_increment

```

Внешний ключ:

```sql

FOREIGN KEY (author_id) REFERENCES authors(author_id)

или при изменении таблицы

ALTER TABLE books ADD FOREIGN KEY (author_id) REFERENCES authors(author_id);

```

### Типы:

- int
- tinyint(1) - замена boolean
- float/double
- decimal(10,2) - Для точных финансовых операций (10 - всего знаков, 2 после запятой)
- varchar(COUNT_CHAR)
- timestamp
- enum(value_1,value_2,value_3) - выбор из списка

Параметры:

- primary key - является ли поле уникальный идентификатор строки в таблице;
- auto_increment - автоматическая генерация номера;
- NULL / NOT NULL - может ли столбец принимать нулевое значение;
- DEFAULT NAME_VALUE - значение по умолчанию;

## Таблицы

Узнать информацию о таблице:

```sql
SHOW COLUMNS from table_name
```

```sql
  DESC table_name
```

Создать:

```sql

CREATE TABLE table_name (column_name_1 type_column_name_1, column_name_2 type_column_2)

```

Удалить:

```sql

DROP TABLE table_name

```

## Столбцы

Добавить:

```sql
ALTER TABLE table_name ADD column_name type_column
```

Удалить:

```sql
  ALTER TABLE table_name DROP COLUMN column_name
```

Изменить тип:

```sql

ALTER TABLE table_name MODIFY COLUMN column_name column_type

```

## Данные

Получить все данные из таблицы:

```sql

SELECT * FROM table_name

```

Получить только конкретные столбцы из таблицы:

```sql
SELECT column_1, column_2 FROM table_name
```

Получить только первые N строк:

```sql
  SELECT * FROM table_name LIMIT N
```

Получить только строки с K по N:

```sql

SELECT * FROM table_name LIMIT N OFFSET K

```

Добавить по всем столбцам:

```sql

INSERT INTO table_name values (value_1, value_2...)

```

Добавить только в определенные столбцы:

```sql
INSERT INTO table_name (column_1, column_2) values (value_1, value_2)
```

Удалить все строки:

```sql
  DELETE FROM table_name
```

Удалить строку:

```sql

DELETE FROM table_name where condition

```

Обновить все строки столбца:

```sql

UPDATE table_name SET column_name_1 = value_1, column_name_2 = value_2

```

Обновить одну строку столбца:

```sql
UPDATE table_name SET column_name = 100 WHERE id = 1
```

## Опции запроса

Сортировка по уменьшению/по возрастанию:

```sql
SELECT * FROM table ORDER BY id DESC/ASC
```

## Транзакции

Начать транзакцию:

```sql
BEGIN/START TRANSACTION
```

Подтвердить транзакцию:

```sql
COMMIT
```

Добавить точку сохранения (точка сохраняет данные в ПРЕДЕЛАХ ТРАНЗАКЦИИ):

```sql
SAVEPOINT NAME_POINT;
```

Полностью откатить транзакцию/ откатить до точки сохранения:

```sql
ROLLBACK / ROLLBACK TO SAVEPOINT NAME_POINT
```

## События

[Документация по событиям](https://www.rldp.ru/mysql/mysqlpro/events.html)

Узнать включен/выключен планировщик событий:

```sql
SHOW VARIABLES LIKE "event_scheduler"
```

Включить/выключить планировщик событий:

```sql
SET GLOBAL event_scheduler = ON/OFF
```

<div>
Включать/выключать планировщик событий вовремя работы сервера нельзя. Для этого нужно приостановить работу mySQL.
</div>

Получить все текущие события:

```sql

SELECT event_name, status, event_definition
FROM information_schema.events
WHERE event_schema="name_data_base";

```

Создание события

```sql

CREATE EVENT name
ON SCHEDULE condition_time
DO
sql_statement;

```

```sql

CREATE EVENT update_subscription_age
ON SCHEDULE EVERY 1 DAY
DO
UPDATE tokens
SET subscription_age = DATEDIFF(NOW(), time_subscribed);

```

Редактирование события

```sql

ALTER EVENT name ON SCHEDULE
new_condition_time;

```

```sql

ALTER EVENT myevent ON SCHEDULE
EVERY 12 HOUR STARTS
CURRENT_TIMESTAMP + 4 HOUR;

```

Отключить событие

```sql
ALTER EVENT name DISABLE;
```

Удаление события

```sql
DROP EVENT name
```
