# Laravel
[Документация](https://laravel.com/docs/)


## Установка
[Статья с установкой в докере](https://timeweb.cloud/tutorials/laravel/kak-nastroit-laravel-nginx-i-mysql-s-pomoschyu-docker-compose#zakluchenie)

## Хелпер функции
[Документация](https://laravel.com/docs/helpers)

Получить значение из конфигурации:
```php
config('name.name')
config('name.name',default_value)
```
Получить app:
```php
app()
```
Создать/получить сервис из контейнера (app):
```php
app()->make('name')
app('name')
```
Для некоторых сервисов существует функции хелперы. Например:
```php
cache()
```
## Фасады
[Список фасадов и соответствующих хелпер-функций](https://laravel.com/docs/12.x/facades#facade-class-reference)

### Service Provider
Создать:
```bash
php artisan make:provider NameServiceProvider
```

### Route
Получить все пути:
```bash
php artisan route:list
```
Получить страницу:
```php
Route::get('/route',callback());
Route::view('/route','view_name');
```
Редирект:
```php
Route::view('/route','redirect_route');
```
Обработка 404:
```php
Route::fallback(callback());
```
## Controllers
[Шаблонные наименование действий контроллеров](https://laravel.su/docs/11.x/controllers#deistviia-vypolniaemye-resursnymi-kontrollerami)

Создание через artisan:
```bash
php artisan make:controller name_controller
```
Создать все crud действия:
```phph
Route::resource('/route',ClassController:class);
```

## Основные команды