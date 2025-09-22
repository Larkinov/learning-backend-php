# VS Code

[[https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf|Шорткаты]]

## Расширения

### PHP Intelephense

### Rest Client

Rest Client - для отправки запросов напрямую через IDE ([Документация](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)):

- Установить расширение;
- Создать файл name.http;
- Написать запрос ([стандарт RFC 26-16](http://www.w3.org/Protocols/rfc2616/rfc2616-sec5.html));
- Нажать "Send Request" над запросом или Ctrl + Alt + R в файле.
  Пример запроса:
  ```http
  POST https://example.com/comments HTTP/1.1
  content-type: application/json
  ```

{
"name": "sample",
"time": "Wed, 21 Oct 2015 18:27:50 GMT"
}

````
Пример двух запросов, которые можно запускать по отдельности:
```http
https://example.com/comments/1

###

https://example.com/topics/1 HTTP/1.1
````
