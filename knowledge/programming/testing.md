# Тестирование

## Краткая теория

Виды тестирований:
- Unit-тестирование / модульное тестирование — проверка самых частей кода (функций, классов) по отдельности;
- Интеграционное тестирование - проверка взаимодействия между различными модулями или компонентами системы. Тестируются интерфейсы и связь между ними.
- Системное тестирование / End-to-end тестирование - тестирование всей системы целиком. Проводится разработчиками или тестировщиками для проверки, как все компоненты работают вместе как единое целое.
- Приемочное тестирование - тестирования ПО, при котором система проверяется на соответствие техническим и бизнес требованиям.

## PHPUnit

PHPUnit - библиотека для тестирования PHP-кода: [официальная документация](https://phpunit.de/documentation.html)

### Install
```bash
composer require --dev phpunit/phpunit
```

### CLI
Команда для запуска тестов:

```bash
/path/to/vendor/bin/phpunit
```

Проверка файла/каталога с кодом. Запуск выведет результаты файлов тестирования:

```bash
/path/to/vendor/bin/phpunit /path/to/file
```

Остановить проверку тестов при первом провальном тестировании:

```bash
/path/to/vendor/bin/phpunit /path/to/file --stop-on-failure
```

### Example
Создание тест-класса:

```php
namespace Tests; //какой-нибудь отдельный namespace для тестов

use PHPUnit\Framework\TestCase; //подключение класса тест кейсов
use Sun\PhpUnitTest\SalaryCalculator;

class SalaryCalculatorTest extends TestCase //наследуемся
{

    /**
     * @dataProvider dataProvider   //data provider - данные передающиеся проверяемой функции
     */
    public function testCalculate(float $salary,float $expected): void
    {
        $salaryCalculator = new SalaryCalculator();

        $result = $salaryCalculator->calculate($salary);  //получаем результат проверяемой функции

        //проверка на полное совпадение результата с $expected
        self::assertEquals($expected, $result);
    }

    //функция массива входных данных
    public static function dataProvider():array{
        return [
            [10,8],
            [20,16],
            [11,8.8],
            [20,16],
            [10,8],
        ];
    }
}
```

### Разное
Специальные функции:

- Выполнение перед запуском каждого теста:

```php
parent::setUp();
```

- Выполнение перед запуском класса теста:

```php
parent::setUpBeforeClass();
```

- Выполнение после работы каждого теста:

```php
parent::tearDown();
```

## Codeception

[Быстрый старт](https://codeception.com/quickstart)

### Установка

```bash
composer require "codeception/codeception" --dev

php vendor/bin/codecept bootstrap - создание конфигурации
```

###
```bash
# запуск всех тестов
php vendor/bin/codecept run --steps

# запуск приемочных тестов
php vendor/bin/codecept init Acceptance

# запуск всех тестов
php vendor/bin/codecept init Api

# запуск всех тестов
php vendor/bin/codecept init Unit

```
### Приемочный тест

```bash
php vendor/bin/codecept generate:cest Acceptance First
```