# json-printer

[![Continuous Deployment](https://github.com/ergebnis/json-printer/workflows/Continuous%20Deployment/badge.svg)](https://github.com/ergebnis/json-printer/actions)
[![Continuous Integration](https://github.com/ergebnis/json-printer/workflows/Continuous%20Integration/badge.svg)](https://github.com/ergebnis/json-printer/actions)
[![Code Coverage](https://codecov.io/gh/ergebnis/json-printer/branch/master/graph/badge.svg)](https://codecov.io/gh/ergebnis/json-printer)
[![Type Coverage](https://shepherd.dev/github/ergebnis/json-printer/coverage.svg)](https://shepherd.dev/github/ergebnis/json-printer)
[![Latest Stable Version](https://poser.pugx.org/ergebnis/json-printer/v/stable)](https://packagist.org/packages/ergebnis/json-printer)
[![Total Downloads](https://poser.pugx.org/ergebnis/json-printer/downloads)](https://packagist.org/packages/ergebnis/json-printer)

Provides a JSON printer, allowing for flexible indentation.

## Installation

Run

```
$ composer require ergebnis/json-printer
```

## Usage

Let's assume we have a variable `$json` which contains some JSON that is not indented:

```json
{"name":"Andreas Möller","emoji":"🤓","urls":["https://localheinz.com","https://github.com/localheinz","https://twitter.com/localheinz"]}
```

or indented with 4 spaces:

```json
{
    "name":"Andreas Möller",
    "emoji":"🤓",
    "urls":[
        "https://localheinz.com",
        "https://github.com/localheinz",
        "https://twitter.com/localheinz"
    ]
}
```

but we want to indent it with 2 spaces (or tabs).

This is where `Ergebnis\Json\Printer\Printer` comes in

```php
use Ergebnis\Json\Printer\Printer;

$printer = new Printer();

$printed = $printer->print(
    $json,
    '  '
);
```

which results in `$printed`:

```json
{
  "name":"Andreas Möller",
  "emoji":"🤓",
  "urls":[
    "https://localheinz.com",
    "https://github.com/localheinz",
    "https://twitter.com/localheinz"
  ]
}
```

:bulb: Note that this printer is only concerned with normalizing the
indentation, no escaping or un-escaping occurs.

## Changelog

Please have a look at [`CHANGELOG.md`](CHANGELOG.md).

## Contributing

Please have a look at [`CONTRIBUTING.md`](.github/CONTRIBUTING.md).

## Code of Conduct

Please have a look at [`CODE_OF_CONDUCT.md`](https://github.com/ergebnis/.github/blob/master/CODE_OF_CONDUCT.md).

## License

This package is licensed using the MIT License.

## Credits

The [`Printer`](src/Printer.php) is adopted from
[`Composer\Json\JsonFormatter`](https://github.com/composer/composer/blob/1.6.0/src/Composer/Json/JsonFormatter.php)
(originally licensed under MIT by [Nils Adermann](https://github.com/naderman)
and [Jordi Boggiano](https://github.com/seldaek)), who adopted it from a
[blog post by Dave Perrett](https://www.daveperrett.com/articles/2008/03/11/format-json-with-php/)
(originally licensed under MIT by [Dave Perrett](https://github.com/recurser)).

The [`PrinterTest`](test/Unit/PrinterTest.php) is inspired
by [`Composer\Test\Json\JsonFormatterTest`](https://github.com/composer/composer/blob/1.6.0/tests/Composer/Test/Json/JsonFormatterTest.php)
(originally licensed under MIT by [Nils Adermann](https://github.com/naderman)
and [Jordi Boggiano](https://github.com/seldaek)), as well as
[`ZendTest\Json\JsonTest`](https://github.com/zendframework/zend-json/blob/release-3.0.0/test/JsonTest.php)
(originally licensed under New BSD License).
