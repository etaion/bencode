# Bencode serialization for Laravel

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Quality Score][ico-code-quality]][link-code-quality]
[![Total Downloads][ico-downloads]][link-downloads]

This library allows developers to encode or decode bencoded data strings in
Laravel. More information about bencode can be found at [Wikipedia](http://en.wikipedia.org/wiki/Bencode).
The format is primarily used in the .torrent file specification.

## Install

Via Composer

``` bash
$ composer require bhutanio/bencode
```

## Usage

### Encoding an array

```php
<?php

use Bhutanio\Bencode\Bencode;

$data = array(
    "string" => "bar",
    "integer" => 42,
    "array" => array(
        "one",
        "two",
        "three",
    ),
);

echo Bencode::encode($data);
```

The above produces the string `d5:arrayl3:one3:two5:threee7:integeri42e6:string3:bare`.

### Decoding a string

```php
<?php

use Bhutanio\Bencode\Bencode;

$string = "d5:arrayl3:one3:two5:threee7:integeri42e6:string3:bare";

print_r(Bencode::decode($string));
```

The above produces the the following output:
```
Array
(
    [array] => Array
        (
            [0] => one
            [1] => two
            [2] => three
        )

    [integer] => 42
    [string] => bar
)
```

## Testing

``` bash
$ cp phpunit.xml.dst phpunit.xml
$ vendor/bin/phpunit -c phpunit.xml
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/bhutanio/bencode.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/bhutanio/bencode.svg?style=flat-square
[ico-coveralls]: https://img.shields.io/coveralls/bhutanio/bencode.svg?style=flat-square
[ico-code-quality]: https://img.shields.io/sensiolabs/i/99e21d84-8d2b-44c5-9107-059e16277ce6.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/bhutanio/bencode.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/bhutanio/bencode
[link-travis]: https://travis-ci.org/bhutanio/bencode
[link-coveralls]: https://coveralls.io/r/bhutanio/bencode
[link-code-quality]: https://insight.sensiolabs.com/projects/99e21d84-8d2b-44c5-9107-059e16277ce6
[link-downloads]: https://packagist.org/packages/bhutanio/bencode
[link-author]: https://github.com/rchouinard
[link-contributors]: https://github.com/bhutanio/bencode/graphs/contributors

