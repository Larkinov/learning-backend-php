 # Postgres 

 ## CLI 

Подключиться к CLI:
```bash
psql -U USERNAME
```

Подключиться к конкретной БД:
```bash
psql -d BASE_NAME
```

Выйти:
```sql
\q
```

Получить все БД:
```sql
\l
```

Подключиться к другой БД:
```sql
\c BASE_NAME
```

Получить всех пользователей:
```sql
\du[+]
```

Узнать поля таблицы:
```sql
\d TABLE_NAME
```

 ## Пользователи 

Добавить пользователя:
```sql

CREATE USER USERNAME WITH PASSWORD 'PASSWORD' [PRIVILEGES];

```

Удалить пользователя:
```sql

DROP USER USERNAME;

```
 ## Привилегии 
Основные типы:
  * SELECT: Позволяет просматривать данные в таблице или представлении.
  * INSERT: Позволяет добавлять новые строки в таблицу.
  * UPDATE: Позволяет изменять существующие строки в таблице.
  * DELETE: Позволяет удалять строки из таблицы.
  * TRUNCATE: Позволяет удалять все строки из таблицы без ведения журнала.
  * REFERENCES: Позволяет создавать ссылки на таблицы (например, в внешних ключах).
  * TRIGGER: Позволяет создавать триггеры, которые позволяют выполнять действия при определенных событиях в таблице.
  * USAGE: Применяется к специальным объектам, таким как схемы и последовательности. Например, разрешает доступ к последовательности.
  * CREATE: Позволяет создавать новые объекты в схеме, например, таблицы или представления.
  * CONNECT: Позволяет пользователю подключаться к базе данных.
  * TEMPORARY: Позволяет создавать временные таблицы в текущем сеансе.

Добавить привилегии:
```sql

GRANT NAME_PRIVILEGES [, NAME_PRIVILEGES_2] ON TABLE TO USERNAME;

```

Добавить все привилегии для таблицы:
```sql

GRANT ALL PRIVILEGES ON TABLE TO USERNAME;

```

Удалить привилегию:
```sql

REVOKE NAME_PRIVILEGES [, NAME_PRIVILEGES_2] ON TABLE TO USERNAME;

```

Удалить все привилегии:
```sql

REVOKE ALL RIVILEGES ON TABLE TO USERNAME;

```

 ## Ключи 

Создать первичный ключ:
```sql

PRIMARY KEY

```

Создать внешний ключ:
```sql

FOREIGN KEY (NAME_COLUMN) REFERENCES TABLE_NAME(TABLE_NAME_COLUMN_NAME)

```

 ## Типы данных 

timestamp - дата и время без часового пояса;

timestamp with time zone - дата и время с часовым поясом;

 ## Базы данных 
 ## Таблицы 

Создать таблицу:
```sql

CREATE TABLE TABLE_NAME (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL
);

```

Переименовать таблицу:
```sql

ALTER TABLE TABLE_NAME RENAME TO NEW_TABLE_NAME;

```

Удалить таблицу:
```sql

DROP TABLE TABLE_NAME;

```

Добавить столбец:
```sql

ALTER TABLE TABLE_NAME
ADD COLUMN NEW_COLUMN_NAME DEFAULT VALUE;;

```

Переименовать столбец:
```sql

ALTER TABLE TABLE_NAME
RENAME COLUMN COLUMN_NAME TO NEW_COLUMN_NAME;

```

Правка ограничений столбец:
```sql

ALTER TABLE TABLE_NAME
ALTER COLUMN COLUMN_NAME SET NEW_LIMITATION;

```

Правка типа столбца:
```sql

ALTER TABLE TABLE_NAME
ALTER COLUMN COLUMN_NAME TYPE NEW_TYPE;

```


 ## Данные 

Добавить данные:
```sql

INSERT INTO TABLE_NAME(COLUMN_NAME) VALUES(VALUE_1);

```

Обновить данные:
```sql

UPDATE TABLE_NAME
SET COLUMN_NAME = NEW_VALUE_1
WHERE COLUMN_NAME = 'Test author';

```

Удалить данные:
```sql

DELETE FROM TABLE_NAME
WHERE COLUMN_NAME LIKE '%_updated';

```