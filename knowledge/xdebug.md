# XDebug

## Подключение для работы в VS Code

### Простое подключение (без профилирования)

1. Установить плагин PHP Debug
2. В настройках php.ini подключить / убрать комментирование:

```
zend_extension = xdebug
xdebug.mode = debug
xdebug.start_with_request = yes
```
3. Открыть вкладку Run and Debug
4. Создать новый launch.json (он автоматически загрузит параметры для дебага)
5. Дебаггинг происходит либо на сервер по умолчанию - localhost:9000, либо в самой IDE:
- Listen for XDebug - прослушивание скрипта PHP в браузере - предварительно нужно поднять веб-сервер
- Launch currently open script - проверка текущего скрипта в IDE
- Launch Built-in web server - проверка с веб-сервером
