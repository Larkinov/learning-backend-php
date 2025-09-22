# Тестирование

**Unit-тестирование** - тестирование отдельных функций, методов и участков кода. \\

**Интеграционное тестирование** - тестирование модулей и их совместной работы. \\

## PHP Unit-тесты

PHPUnit - библиотека для тестирования PHP-кода: [официальная документация](https://phpunit-documentation-russian.readthedocs.io/ru/latest/index.html)

Установка composer:

```bash
composer require --dev phpunit/phpunit
```

Основная команда для запуска тестов:

```bash
/path/to/vendor/bin/phpunit
```

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

Проверка файла/каталога с кодом. Запуск выведет результаты файлов тестирования:

```bash
/path/to/vendor/bin/phpunit /path/to/file
```

Остановить проверку тестов при первом провальном тестировании:

```bash
/path/to/vendor/bin/phpunit /path/to/file --stop-on-failure
```

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
