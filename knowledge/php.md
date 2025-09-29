# PHP

[Официальная документация](https://www.php.net/)

## Строки

Синтаксис Nowdoc (текст с одинарными кавычками):

```php
$str = <<<'EOD'
Example of string
spanning multiple lines
using nowdoc syntax.
$a does not parse.
EOD;
```

Синтаксис Heredoc (текст с двойными кавычками):

```php
$str = <<<EOD
Example of string
spanning multiple lines
using nowdoc syntax.
$a does not parse.
EOD;
```

## Регулярные выражения

https://archive-ipq-co.narod.ru/l1/regexp.html

## PDO

Вернуть объекты класса заполненные через конструктор

```php
$sth->fetchAll(\PDO::FETCH_CLASS, $className, array_keys($params));
```

## Разное

Вызов CLI в Linux:
`phpphp -a`

escapeshellcmd - функция может ломать команды с фоновым запуском!

# Различные библиотеки

[Работа с .env](https://github.com/vlucas/phpdotenv)

[Легкая библиотека для работы с Telegram](https://nutgram.dev/docs/introduction)

[Подключение Xdebug](https://ilyachalov.livejournal.com/300231.html) и последующие статьи оттуда же